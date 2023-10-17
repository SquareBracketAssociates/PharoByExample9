## Seaside by example
	baseline:'Seaside3';
	repository: 'github://SeasideSt/Seaside:master/repository';
	load
    removeParent: WADevelopmentConfiguration instance
	html text: 'hello world'
	^ true
world_ application.
count` won't work. This is because the object named by `count` is an integer,
html html: '&ndash;'.     "render an HTML incantation"
html render: 1.              "render any object"
	html heading: 'Rendering Demo'.
	html heading
		level: 2;
		with: 'Rendering basic HTML: '.
	html div
		class: 'subcomponent';
		with: htmlDemo.
	"render the remaining components ..."
	^ { htmlDemo . formDemo . editDemo . dialogDemo }
	self renderParagraphsOn: html.
	self renderListsAndTablesOn: html.
	self renderDivsAndSpansOn: html.
	self renderLinkWithCallbackOn: html
	html paragraph: 'A plain text paragraph.'.
	html paragraph: [
		html
			text: 'A paragraph with plain text followed by a line break. ';
			break;
			emphasis: 'Emphasized text ';
			text: 'followed by a horizontal rule.';
			horizontalRule;
			text: 'An image URI: '.
		html image
			url: self squeakImageUrl;
			width: '50']
	html orderedList: [
		html listItem: 'An ordered list item'].
	html unorderedList: [
		html listItem: 'An unordered list item'].
	html table: [
		html tableRow: [
			html tableData: 'A table with one data cell.']]
	html div
		id: 'author';
		with: [
			html text: 'Raw text within a div with id ''author''. '.
			html span
				class: 'highlight';
				with: 'A span with class ''highlight''.']
	html paragraph: [
		html text: 'An anchor with a local action: '.
		html span with: [
			html anchor
				callback: [toggleValue := toggleValue not];
				with: 'toggle boolean:'].
		html space.
		html span
			class: 'boolean';
			with: toggleValue ]
	| radioGroup |
	html heading: heading.
	html form: [
		html span: 'Heading: '.
		html textInput on: #heading of: self.
		html select
			list: self colors;
			on: #color of: self.
		radioGroup := html radioGroup.
		html text: 'Radio on:'.
		radioGroup radioButton
			selected: radioOn;
			callback: [radioOn := true].
		html text: 'off:'.
		radioGroup radioButton
			selected: radioOn not;
			callback: [radioOn := false].
		html checkbox on: #checked of: self.
		html submitButton
			text: 'done' ]
SeasideDemoWidget >> style
	^ '
body {
	font: 10pt Arial, Helvetica, sans-serif, Times New Roman;
}
h2 {
	font-size: 12pt;
	font-weight: normal;
	font-style: italic;
}
table { border-collapse: collapse; }
td {
	border: 2px solid #CCCCCC;
	padding: 4px;
}
#author {
	border: 1px solid black;
	padding: 2px;
	margin: 2px;
}
.subcomponent {
	border: 2px solid lightblue;
	padding: 2px;
	margin: 2px;
}
.highlight { background-color: yellow; }
.boolean { background-color: lightgrey; }
.field { background-color: lightgrey; }
'
callee`. The caller is temporarily replaced by the callee, until the callee
	html span
		class: 'field';
		with: self text.
	html space.
	html anchor
		callback: [self text: (self call: (SeasideEditAnswerDemo new text: self text))];
		with: 'edit'
	html form: [
		html textInput
			on: #text of: self.
		html submitButton
			callback: [ self answer: self text ];
			text: 'ok'.
		]
	html anchor
		callback: [ self request: 'edit this' label: 'done' default: 'some text' ];
		with: 'self request:'.
...
	html space.
	html anchor
		callback: [ self inform: 'yes!' ];
		with: 'self inform:'.
...
	html space.
	html anchor
		callback: [
			(self confirm: 'Are you happy?')
				ifTrue: [ self inform: ':-)' ]
				ifFalse: [ self inform: ':-(' ]
			];
		with: 'self confirm:'.
	[ self chooseCheese.
	  self confirmCheese ] whileFalse.
	self informCheese
	cheese := self
		chooseFrom: #('Greyerzer' 'Tilsiter' 'Sbrinz')
		caption: 'What''s your favorite Cheese?'.
	cheese isNil ifTrue: [ self chooseCheese ]
	^self confirm: 'Is ', cheese,  ' your favorite cheese?'
	self inform: 'Your favorite cheese is ', cheese, '.'
	"... render the title bar ..."
	html div id: 'body'; with: task
	| shipping billing creditCard |
	cart := WAStoreCart new.
	self isolate:
		[[ self fillCart.
		self confirmContentsOfCart ]
			whileFalse ].

	self isolate:
		[ shipping := self getShippingAddress.
		billing := (self useAsBillingAddress: shipping)
					ifFalse: [ self getBillingAddress ]
					ifTrue: [ shipping ].
		creditCard := self getPaymentInfo.
		self shipTo: shipping billTo: billing payWith: creditCard ].

	self displayConfirmation.
	self inform: 'Before parent txn'.
	self isolate:
			[self inform: 'Inside parent txn'.
			self isolate: [self inform: 'Inside child txn'].
			self inform: 'Outside child txn'].
	self inform: 'Outside parent txn'
	super initialize.
	contents := OrderedCollection new.
	stack
		push: 3;
		push: 4;
		div.
	self assert: stack size = 1.
	self assert: stack top = (4/3).
	^ 'table.keypad { float: left; }
td.key {
	border: 1px solid grey;
	background: lightgrey;
	padding: 4px;
	text-align: center;
}
table.stack { float: left; }
td.stackcell {
	border: 2px solid white;
	border-left-color: grey;
	border-right-color: grey;
	border-bottom-color: grey;
	padding: 4px;
	text-align: right;
}
td.small { font-size: 8pt; }'
	html tableData
		class: 'key';
		colSpan: anInteger;
		with:
				[ html anchor
					callback: aBlock;
					with: [ html html: text ]]
	self
		renderStackButton: text
		callback: aBlock
		colSpan: 1
		on: html
  self ensureStackMachineNotEmpty.
  html table
    class: 'keypad';
    with: [
      html tableRow: [
          self renderStackButton: '+' callback: [self stackOp: #add] on: html.
          self renderStackButton: '&ndash;' callback: [self stackOp: #min] on: html.
          self renderStackButton: '&times;' callback: [self stackOp: #mul] on: html.
          self renderStackButton: '&divide;' callback: [self stackOp: #div] on: html.
          self renderStackButton: '&plusmn;' callback: [self stackOp: #neg] on: html ].
        html tableRow: [
          self renderStackButton: '1' callback: [self type: '1'] on: html.
          self renderStackButton: '2' callback: [self type: '2'] on: html.
          self renderStackButton: '3' callback: [self type: '3'] on: html.
          self renderStackButton: 'Drop' callback: [self stackPopIfNotEmpty]
          	colSpan: 2 on: html ].
" and so on ... "
        html tableRow: [
          self renderStackButton: '0' callback: [self type: '0'] colSpan: 2 on: html.
          self renderStackButton: 'C' callback: [self stackClearTop] on: html.
          self renderStackButton: 'Enter'
          	callback: [self stackOp: #dup. self setClearMode]
			colSpan: 2 on: html ]]
	stackMachine push: (self stackPopTopOrZero asString, aString) asNumber.
	^ stackMachine isEmpty
		ifTrue: [ 0 ]
		ifFalse: [ stackMachine pop ]
	stackMachine isEmpty
		ifFalse: [ stackMachine pop ]
	[ stackMachine perform: op ] on: AssertionFailure do: [ ].
	self inPushMode ifTrue: [
		stackMachine push: stackMachine top.
		self stackClearTop ].
	self inClearMode ifTrue: [ self stackClearTop ].
	stackMachine push: (self stackPopTopOrZero asString, aString) asNumber.
	callback: [ self call: (MyDisplayStack new setMyStackMachine: stackMachine)];
	with: 'open'
	callback: [ self answer];
	with: 'close'
	html div id: 'keypad'; with: keypad.
	html div id: 'display'; with: display.
	html tableData
		class: 'key';
		colSpan: anInteger;
		with: [
			html anchor
				callback: aBlock;
				onClick:				"handle Javascript event"
					(html scriptaculous updater
						id: 'display';
						callback: [ :r |
							aBlock value.
							r render: display ];
						return: false);
				with: [ html html: text ] ]
	(WAAdmin register: self asApplicationAt: self applicationName)
		addLibrary: PTDevelopmentLibrary
	'display',
	'http://localhost/seaside/RPN+Calculator',
	{'evalScripts': true,
	  'parameters': ['UNDERSCOREs=zcdqfonqwbeYzkza', 'UNDERSCOREk=jMORHtqr','9'].join('&')});
return false