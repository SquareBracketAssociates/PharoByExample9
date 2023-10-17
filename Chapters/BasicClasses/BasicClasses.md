## Basic classes
Object class selectors size   "Count the class methods"
>>> 'an OpalCompiler'
	| name |
	(name := self name).
	name = #unnamed
		ifFalse: [
			^ aStream
				nextPutAll: 'Color ';
				nextPutAll: name ].
	self storeOn: aStream
>>> 'Color red'
>>> true
>>> (3@4)
>>> $a
>>> #(1 2 3)
>>> Color red
>>> {(10@10). (100@100)}
>>> an Array(an OpalCompiler (100@100))
>>> #(10 #@ 10 100 #@ 100)
	"The receiver prints on aStream in terms of infix notation."

	aStream nextPut: $(.
	x printOn: aStream.
	aStream nextPut: $@.
	(y notNil and: [y negative])
		ifTrue: [
			"Avoid ambiguous @- construct"
			aStream space ].
	y printOn: aStream.
	aStream nextPut: $).
    aStream nextPut: $(;
        print: start;
        nextPutAll: ' to: ';
        print: stop.
    step ~= 1 ifTrue: [aStream nextPutAll: ' by: '; print: step].
    aStream nextPut: $)
>>> (1 to: 10)    "intervals are self-evaluating"
    "Answer whether the receiver and the argument represent the same object.
    If = is redefined in any subclass, consider also redefining the message hash."

    ^ self == anObject
>>> true
>>> true
>>> SmallInteger
>>> true
>>> true
>>> true
>>> true
>>> false
>>> true
>>> false
>>> false
a1
>>> #(#('harry'))
a2
>>> #(#('harry'))
a1
>>> #(#('sally'))
>>> #(#('sally'))    "the subarray is shared!"
a2 := a1 deepCopy.
(a1 at: 1) at: 1 put: 'sally'.
a1
>>> #(#('sally'))
>>> #(#(#('harry')))
a2 := { a1 }.
a1 at: 1 put: a2.
a1 deepCopy
>>> !''... does not terminate!''!
	"Answer another instance just like the receiver.
	Subclasses typically override postCopy;
	they typically do not override shallowCopy."

	^ self shallowCopy postCopy
	^ self
    "Return the first element and remove it from the stack."

    self assert: [ self isNotEmpty ].
    ^ self linkedList removeFirst element
subclassResponsibility`.
    "This message sets up a framework for the behavior of the class' subclasses.
    Announce that the subclass should have implemented this message."

    SubclassResponsibility signalFor: thisContext sender selector
>>> !''Error: Number is an abstract class. Make a concrete subclass.''!
   "Subclasses should redefine this method to perform initializations on instance creation"
    "Answer a new initialized instance of the receiver (which is a class) with no indexable
    variables. Fail if the class is indexable."
    ^ self basicNew initialize
    "Answer whether the receiver is less than the argument."

    ^ self subclassResponsibility

Magnitude >> > aMagnitude
    "Answer whether the receiver is greater than the argument."

    ^ aMagnitude < self
methods_ which generate `Duration`s, such as `hour`, `day` and `week`.
>>> 3.5             "Addition of two numbers"
>>> 17.0           "Multiplication of two numbers"
>>> 4                 "Division of two numbers"
>>> 1.7              "Subtraction of two numbers"
>>> false           "Equality between two numbers"
>>> true            "Test if two numbers are different"
>>> true            "Greater than"
>>> true            "Greater or equal  than"
>>> false           "Smaller than"
>>> 100@10    "Point creation"
>>> 1000
>>> 3.141592653589793
>>> Float infinity
>>> true
>>> (3/4)
>>> Fraction
>>> 3
>>> true
>>> true
>>> LargePositiveInteger
>>> LargeNegativeInteger
n := 2.
3 timesRepeat: [ n := n * n ].
n
>>> 256
>>> true
class>>value:` takes the Unicode \(or ASCII\) integer value as argument and
>>> true
>>> Character home
>>> Character value: 2
>>> Character space
>>> $a
>>> 'a'
>>> $a
>>> '$a'
>>> true
>>> ByteString
>>> false
>>> true
>>> 'hullo'
>>> Error: symbols can not be modified.
>>> 5
>>> true
	ifTrue: [ 'bigger' ]
	ifFalse: [ 'smaller' ]
>>> 'bigger'
    ^ trueAlternativeBlock value

False >> ifTrue: trueAlternativeBlock ifFalse: falseAlternativeBlock
    ^ falseAlternativeBlock value
    "Negation--answer false since the receiver is true."
    ^ false

False >> not
    "Negation--answer true since the receiver is false."
    ^ true
>>> false    "Eager, must evaluate both sides"
>>> false    "Lazy, only evaluate receiver"
>>> false    "argument block is never executed, so no exception"