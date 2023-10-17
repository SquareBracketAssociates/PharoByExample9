## SUnit: Tests in Pharo
time._ 
it should appear to the client code_, rather than about how to implement it.
	instanceVariableNames: 'full empty'
	classVariableNames: ''
	package: 'MySetTest'
	empty := Set new.
	full := Set with: 5 with: 6
	self assert: (full includes: 5).
	self assert: (full includes: 6)
	self assert: (empty occurrencesOf: 0) equals: 0.
	self assert: (full occurrencesOf: 5) equals: 1.
	full add: 5.
	self assert: (full occurrencesOf: 5) equals: 1
	full remove: 5.
	self assert: (full includes: 6).
	self deny: (full includes: 5)
tests \(t\)_ or press the icon.
#testRemove`.
	full remove: 5.
	self assert: (full includes: 6).
	self deny: (full includes: 5)
	full remove: 5.
	self assert: (full includes: 7).
	self deny: (full includes: 5)

MyExampleSetTest debug: #testRemove
	self assert: aDateAndTime asDate = ('February 29, 2004' asDate translateTo: 2 hours).
	self
		assert: aDateAndTime asDate
		equals: ('February 29, 2004' asDate translateTo: 2 hours).

	| newCompiledMethod originalCompiledMethod |
	(Smalltalk globals hasClassNamed: #Compiler) ifFalse: [ ^ self skip ].
	...
		self should: [ empty at: 5 ] raise: Error.
		self should: [ empty at: 5 put: #zork ] raise: Error
>>> 1 run, 1 passed, 0 failed, 0 errors
>>> 4 run, 4 passed, 0 failed, 0 errors