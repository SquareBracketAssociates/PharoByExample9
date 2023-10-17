## Building a little game
	instanceVariableNames: 'mouseAction'
	classVariableNames: ''
	package: 'PBE-LightsOut'
	super initialize.
	self label: ''.
	self borderWidth: 2.
	bounds := 0 @ 0 corner: 16 @ 16.
	offColor := Color paleYellow.
	onColor := Color paleBlue darker.
	self useSquareCorners.
	self turnOff
	instanceVariableNames: ''
	classVariableNames: ''
	package: 'PBE-LightsOut'
	| sampleCell width height n |
	super initialize.
	n := self cellsPerSide.
	sampleCell := LOCell new.
	width := sampleCell width.
	height := sampleCell height.
	self bounds: (5 @ 5 extent: (width * n) @ (height * n) + (2 * self borderWidth)).
	cells := Array2D
        new: n
        tabulate: [ :i :j | self newCellAt: i at: j ]
	"The number of cells along each side of the game"
	^ 10
	| sampleCell width height n |
	super initialize.
	n := self cellsPerSide.
	sampleCell := LOCell new.
	width := sampleCell width.
	height := sampleCell height.
	self bounds: (50 @ 50 extent: (width * n) @ (height * n) + (2 * self borderWidth)).
	cells := Array2D 
		new: n 
		tabulate: [ :i :j | self newCellAt: i at: j ]

	"Create a cell for position (i,j) and add it to my on-screen representation at the appropriate screen position. Answer the new cell"

	| c origin |
	c := LOCell new.
	origin := self innerBounds origin.
	self addMorph: c.
	c position: ((i - 1) * c width) @ ((j - 1) * c height) + origin.
	c mouseAction: [ self toggleNeighboursOfCellAt: i at: j ].

	i > 1
		ifTrue: [ (cells at: i - 1 at: j) toggleState ].
	i < self cellsPerSide
		ifTrue: [ (cells at: i + 1 at: j) toggleState ].
	j > 1
		ifTrue: [ (cells at: i at: j - 1) toggleState ].
	j < self cellsPerSide
		ifTrue: [ (cells at: i at: j + 1) toggleState ]
	mouseAction := aBlock

    self toggleState.
	mouseAction value
	"Create a cell for position (i,j) and add it to my on-screen representation at the appropriate screen position. Answer the new cell"

	| c origin |
	c := LOCell new.
	origin := self innerBounds origin.
	self addMorph: c.
	c position: ((i - 1) * c width) @ ((j - 1) * c height) + origin.
	c mouseAction: [ self toggleNeighboursOfCellAt: i at: j ].
	^ c