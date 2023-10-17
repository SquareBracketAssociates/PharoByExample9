## Reflection
w inspect
300@300 )` in it as shown in Figure *@fig:playgroundInspector@* and then
>>>
#(#dependents #announcer #owner #adapter #needRebuild #eventHandler #application #focusOrder 
 #contextKeyBindings #windowIcon #aboutText #askOkToClose #titleHolder #additionalSubpresentersMap 
 #layout #visible #extent #styles #millerList #model #lastPageSelectedTabName #withHeaderBar)
w class allInstVarNames collect: [:each | each -> (w instVarNamed: each)]
	select: [ :each |
				| own |
				own := (each instVarNamed: 'owner').
				own isNotNil and: [ own  isWorldMorph ]]
	"Primitive. Answer a fixed variable in an object. ..."

	<primitive: 173 error: ec>
	self primitiveFailed
	"Primitive. Multiply the receiver by the argument and answer with the
	result if it is a SmallInteger. Fail if the argument or the result is not a
	SmallInteger. Essential. No Lookup. See Object documentation whatIsAPrimitive."

	<primitive: 9>
	^ super * aNumber
>>> SmallFloat64
>>> true
>>> true
>>> false
>>> true    "since Number implements floor"
>>> 1
>>> true    "exception classes can be grouped"
Morph allSuperclasses size.
>>> 2
Morph allSelectors size.
>>> 1442
Morph allInstVarNames size.
>>> 6
Morph selectors size.
>>> 931
Morph instVarNames size.
>>> 6
Morph subclasses size.
>>> 73
Morph allSubclasses size.
>>>  445
Morph linesOfCode.
>>> 5088
>>> (-1@-1)
>>> #('collection' 'position'  ...)
>>> 58514
>>>  138962
>>> #(#octantOf: #roundDownTo: #+ #asIntegerPoint #transposed ...)
>>> #(#fromSton: #setX:setY: #setR:degrees: #bitShiftPoint:)
>>> #(#+)
>>> Object
>>> #()
default` returns an instance you can use to navigate the system. For example:
>>> an OrderedCollection(Object)
>>>43985
>>> 37
>>> 335
	browseMethodsWithSourceString: 'super' 
	matchCase: true
	browseAllSelect: [:method | method sendsToSuper ]
aClass := SmallInteger.
aClass methodDict keys select: [ :aMethod |
  (aClass superclass canUnderstand: aMethod) not ]
>>> an IdentitySet(#threeDigitName #printStringBase:nDigits: ...)
aClass := Number.
aClass methodDict keys select: [ :aMethod |
  (aClass>>aMethod) isAbstract ]
>>>  #(#* #asFloat #storeOn:base: #printOn:base: #+ #round: #/ #- #adaptToInteger:andSend: #nthRoot: #sqrt #adaptToFraction:andSend:)
SystemNavigation default
  browseMessageList: (class withAllSubclasses gather: [ :each |
    each methodDict associations
      select: [:assoc | assoc value sendsToSuper ]
      thenCollect: [:assoc | RGMethodDefinition realClass: each selector: assoc key]])
  name: 'Supersends of ', class name, ' and its subclasses'
>>> #=
	selectMethods: [:method | method sendsToSuper])
	browse.
	selectMethods: [:method |
		method sendsToSuper
		and: [(method parseTree superMessages includes: method selector) not]])
	
error:ec>` defined in the `Object>>#instVarAt:` method. 
	<ignoreForCoverage>
	"self showDocumentation"

	^ 'This package provides function.... "
>>> an Array(<ignoreForCoverage>)
>>> an Array(<primitive: 541>)
>>> an Array(<ignoreForCoverage> <ignoreForCoverage>)
	"Answer the factorial of the receiver."
	self = 0 ifTrue: [thisContext inspect. self halt. ^ 1].
	self > 0 ifTrue: [^ self * (self - 1) slowFactorial].
	self error: 'Not valid for negative integers'
	"This message sets up a framework for the behavior of the class' subclasses.
	Announce that the subclass should have implemented this message."

	SubclassResponsibility signalFor: thisContext sender selector
     "Add this morph to the world."
     self halt.
     self openInWorld: self currentWorld
   "Add this morph to the world."
   self haltIf: #testOpenInWorld.
   self openInWorld: self currentWorld
	<debuggerCompleteToSender>
	Halt if: condition.
	| cntxt |
	cntxt := haltSenderContext.
	[ cntxt isNil ] whileFalse: [
		cntxt selector = aSelector ifTrue: [ self signalIn: haltSenderContext ].
		cntxt := cntxt sender ]
itself_ the message `doesNotUnderstand:` with the message selector as its
	instanceVariableNames: 'subject invocationCount'
	classVariableNames: ''
	package: 'PBE-Reflection'
>>> 479
	invocationCount := 0.
	subject := self.
	^ invocationCount
	Transcript show: 'performing ', aMessage printString; cr.
	invocationCount := invocationCount + 1.
	^ aMessage sendTo: subject
LoggingProxy new become: point.
>>> 0
>>> 4@6
>>> 1
>>> LoggingProxy
- < > <= >= = ~= * / \\ =\=
@ bitShift: // bitAnd: bitOr:
at: at:put: size
next nextPut: atEnd
blockCopy: value value: do: new new: x y
and: or:
whileFalse: whileTrue: whileFalse whileTrue
to:do: to:by:do:
caseOf: caseOf:otherwise:
ifNil: ifNotNil:  ifNil:ifNotNil: ifNotNil:ifNil:
LoggingProxy new become: point.
point invocationCount
>>> 0
>>> 1@2 corner: 3@4
>>> 1
	"Answer a Rectangle that encompasses the receiver and aPoint. 
	This is the most general infix way to create a rectangle."

	^ Rectangle
		point: self
		point: aPoint
	instanceVariableNames: 'x'
	classVariableNames: ''
	package: 'PBE-Reflection'
	| messageName |
	messageName := aMessage selector asString.
	(self class instVarNames includes: messageName)
		ifTrue: [
			self class compile: messageName, String cr, ' ^ ', messageName.
			^ aMessage sendTo: self ].
	^ super doesNotUnderstand: aMessage
myDA x
>>> nil
	"answer the result of sending this message to receiver"

	^ receiver perform: selector withArguments: args
>>> 120
>>> 720
>>> 6
	instanceVariableNames: ''
	classVariableNames: ''
	package: 'PBE-Reflection'
	at: #answer42 
	put: ObjectsAsMethodsExample new
>>> 42
	^ self perform: oldSelector withArguments: arguments
	^ 42