## A first tutorial: Developing a simple counter
counter := Counter new.
counter increment; increment.
counter decrement.
counter count = 1
      instanceVariableNames: 'count'
      classVariableNames: ''
      package: 'MyCounter'
Its API is 
- `decrement` and `increment`
- `count`
Its creation message is `startAt:`
   ^ count
>>> nil
c := Counter new count: 7.
c count
>>> 7
      instanceVariableNames: ''
      classVariableNames: ''
      package: 'MyCounter'
   | c |
   c := Counter new.
   c count: 7.
   self assert: c count equals: 7
   | c |
   c := Counter new.
   c count: 0 ; increment; increment.
   self assert: c count equals: 2
   count := count + 1
   count := count - 1
>>> nil
   self assert: Counter new count equals: 0
  "set the initial value of the value to 0"

  "Your code here""
	self assert: (Counter startingAt: 5) count equals: 5
	^ self new count: anInteger.  
  self assert: ((Counter startingAt: 19) increment ; count) equals: 20
>>> a Counter
   super printOn: aStream.
   aStream nextPutAll: ' with value: ', count printString.
>>> a Counter with value: 0