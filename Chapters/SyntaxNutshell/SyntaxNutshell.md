## Syntax in a nutshell

   (DayNames includes: aSymbol)
      ifTrue: [ StartDay := aSymbol ]
      ifFalse: [ self error: aSymbol, ' is not a recognised day name' ]
modulo:`\), each ending with a colon and taking a single argument. In the
>>> 128
>>> 9
>>> 7
Transcript show: 'hello world'.
Transcript cr
	cr;
	show: 'hello world';
	cr
	"Answer the number of lines represented by the receiver, where every cr adds one line."

	| cr count |
	cr := Character cr.
	count := 1 min: self size.
	self do: [:c | c == cr ifTrue: [count := count + 1]].
	^ count
>>> 3
>>> 33
>>> 3
>>> 3
	| z |
	z := x + y.
	z ] value: 1 value: 2
>>> 3
x := 1.
[ :y | x + y ] value: 2
>>> 3
	ifTrue: [ 'bigger' ]
	ifFalse: [ 'smaller' ]
>>>'bigger'
[ n < 1000 ] whileTrue: [ n := n*2 ].
n
>>> 1024
[ n > 1000 ] whileFalse: [ n := n*2 ].
n
>>> 1024
10 timesRepeat: [ n := n*2 ].
n
>>> 1024
1 to: 10 do: [:n | result := result, n printString, ' '].
result
>>> '1 2 3 4 5 6 7 8 9 10 '
(1 to: 10) do: [:n | result := result, n printString, ' '].
result
>>> '1 2 3 4 5 6 7 8 9 10 '
>>> #(1 4 9 16 25 36 49 64 81 100)
>>> 'eoee'
>>> 'hll thr'
>>> $e
>>> 55
 aNumber
	"Primitive. Add the receiver to the argument and answer with the result
	if it is a SmallInteger. Fail if the argument or the result is not a
	SmallInteger Essential No Lookup. See Object documentation whatIsAPrimitive."

	<primitive: 1>
	^ super + aNumber