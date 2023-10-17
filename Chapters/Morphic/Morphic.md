## Morphic
joe openInWorld.
bill := Morph new color: Color red.
bill openInWorld.
position: (joe position + (10@3))` repeatedly \(see Figure *@fig:moveJoe@*\).
joe addMorph: balloon.
balloon position: joe position.
	instanceVariableNames: ''
	classVariableNames: ''
	package: 'PBE-Morphic'
	| crossHeight crossWidth horizontalBar verticalBar |
	crossHeight := self height / 3.
	crossWidth := self width / 3.
	horizontalBar := self bounds insetBy: 0 @ crossHeight.
	verticalBar := self bounds insetBy: crossWidth @ 0.
	aCanvas fillRectangle: horizontalBar color: self color.
	aCanvas fillRectangle: verticalBar color: self color
	| crossHeight crossWidth horizontalBar verticalBar |
	crossHeight := self height / 3.
	crossWidth := self width / 3.
	horizontalBar := self bounds insetBy: 0 @ crossHeight.
	verticalBar := self bounds insetBy: crossWidth @ 0.
	^ (horizontalBar containsPoint: aPoint) or: [ verticalBar containsPoint: aPoint ]
	| crossHeight |
	crossHeight := self height / 3.
	^ self bounds insetBy: 0 @ crossHeight
	| crossWidth |
	crossWidth := self width / 3.
	^ self bounds insetBy: crossWidth @ 0
	aCanvas fillRectangle: self horizontalBar color: self color.
	aCanvas fillRectangle: self verticalBar color: self color
	^ (self horizontalBar containsPoint: aPoint) or: [ self verticalBar containsPoint: aPoint ]
   bounds: (0@0 corner: 200@200);
   color: (Color blue alpha: 0.4)
	| topAndBottom |
	aCanvas fillRectangle: self horizontalBar color: self color.
	topAndBottom := self verticalBar areasOutside: self horizontalBar.
	topAndBottom do: [ :each | aCanvas fillRectangle: each color: self color ]
	| crossHeight |
	crossHeight := (self height / 3) rounded.
	^ self bounds insetBy: 0 @ crossHeight
	| crossWidth |
	crossWidth := (self width / 3) rounded.
	^ self bounds insetBy: crossWidth @ 0
	^ true
	anEvent redButtonPressed
		ifTrue: [ self color: Color red ].	"click"
	anEvent yellowButtonPressed
		ifTrue: [ self color: Color yellow ].	"action-click"
	self changed
	^ true
	anEvent hand newKeyboardFocus: self
	anEvent hand releaseKeyboardFocus: self
	^ true
	| key |
	key := anEvent key.
	key = KeyboardKey up ifTrue: [ self position: self position - (0 @ 10) ].
	key = KeyboardKey down ifTrue: [ self position: self position + (0 @ 10) ].
	key = KeyboardKey right ifTrue: [ self position: self position + (10 @ 0) ].
	key = KeyboardKey left ifTrue: [ self position: self position - (10 @ 0) ].
		anEvent keyCharacter == $d ifTrue: [ 
			self position: self position + (0 @ 10) ] ]
	^ 100
	(self color diff: Color black) < 0.1
		ifTrue: [ self color: Color red ]
		ifFalse: [ self color: self color darker ]
startStepping` in the small pane at the bottom, and `Do it`.
	super initialize.
	self startStepping
	^ true
	| keyValue |
	keyValue := anEvent keyCharacter.
	keyValue == $+ ifTrue: [ self startStepping ].
	keyValue == $- ifTrue: [ self stopStepping ]
	request: 'What''s your name?'
	initialAnswer: 'no name'
	chooseFrom: #('circle' 'oval' 'square' 'rectangle' 'triangle')
	lines: #(2 4) message: 'Choose a shape'
	instanceVariableNames: ''
	classVariableNames: ''
	package: 'PBE-Morphic'
	super initialize.
	color := Color red.
	bounds := 0 @ 0 extent: 200 @ 200
	^ aMorph color = Color blue
	^ (self wantsDroppedMorph: aMorph event: anEvent) not
    bounds: (100@100 corner: 200@200).
EllipseMorph new openInWorld.
	instanceVariableNames: ''
	classVariableNames: ''
	package: 'PBE-Morphic'
	super initialize.
	color := Color blue.
	self position: 250 @ 100
	| h |
	h := anEvent hand.
	WorldState addDeferredUIMessage: [ h grabMorph: self ].
	anEvent wasHandled: true
morph := (DroppedMorph new color: Color blue) openInWorld.
morph position: (morph position + (70@0)).
(DroppedMorph new color: Color green) openInWorld.
	instanceVariableNames: 'faces dieValue isStopped'
	classVariableNames: ''
	package: 'PBE-Morphic'
	^ self new faces: aNumber
	super initialize.
	self extent: 50 @ 50.
	self
		useGradientFill;
		borderWidth: 2;
		useRoundedCorners.
	self setBorderStyle: #complexRaised.
	self fillStyle direction: self extent.
	self color: Color green.
	dieValue := 1.
	faces := 6.
	isStopped := false
	"Set the number of faces"

	((aNumber isInteger and: [ aNumber > 0 ]) and: [ aNumber <= 9 ])
		ifTrue: [ faces := aNumber ]
	^ {(0.5 @ 0.5)}
	^{0.25@0.25 . 0.75@0.75}
	^{0.25@0.25 . 0.75@0.75 . 0.5@0.5}
	^{0.25@0.25 . 0.75@0.25 . 0.75@0.75 . 0.25@0.75}
	^{0.25@0.25 . 0.75@0.25 . 0.75@0.75 . 0.25@0.75 . 0.5@0.5}
	^{0.25@0.25 . 0.75@0.25 . 0.75@0.75 . 0.25@0.75 . 0.25@0.5 . 0.75@0.5}
	^{0.25@0.25 . 0.75@0.25 . 0.75@0.75 . 0.25@0.75 . 0.25@0.5 . 0.75@0.5 . 0.5@0.5}
	^{0.25@0.25 . 0.75@0.25 . 0.75@0.75 . 0.25@0.75 . 0.25@0.5 . 0.75@0.5 . 0.5@0.5 . 0.5@0.25}
	^{0.25@0.25 . 0.75@0.25 . 0.75@0.75 . 0.25@0.75 . 0.25@0.5 . 0.75@0.5 . 0.5@0.5 . 0.5@0.25 . 0.5@0.75}
	super drawOn: aCanvas.
	(self perform: ('face', dieValue asString) asSymbol)
		do: [ :aPoint | self drawDotOn: aCanvas at: aPoint ]
dieValue asString) asSymbol`. 
	aCanvas
		fillOval: (Rectangle
			center: self position + (self extent * aPoint)
			extent: self extent / 6)
		color: Color black
	((aNumber isInteger and: [ aNumber > 0 ]) and: [ aNumber <= faces ])
		ifTrue: [
			dieValue := aNumber.
			self changed ]
	^ 100
	isStopped ifFalse: [self dieValue: (1 to: faces) atRandom]
	^ true
	anEvent redButtonPressed
		ifTrue: [isStopped := isStopped not]
	| theCanvas |
	theCanvas := aCanvas asAlphaBlendingCanvas: 0.5.
	super drawOn: theCanvas.
	(self perform: ('face', dieValue asString) asSymbol)
		do: [:aPoint | self drawDotOn: theCanvas at: aPoint]