## Traits: reusable class fragments
	 uses: {}
	 package: 'Traits-Example'
	^ 'I''m flying!'
	uses: TFlyingAbility
	instanceVariableNames: ''
	classVariableNames: ''
	package: 'Traits-Example'
>>> 'I''m flying!'
	uses: {}
	package: 'Traits-Example'
	^ 'Hello ', self name
	uses: TGreetable
	instanceVariableNames: ''
	classVariableNames: ''
	package: 'Traits-Example'	
	^ 'Bob'
>>> 'Hello Bob'
	uses: {}
	package: 'Traits-Example'
	^ self
	uses: TInspector
	instanceVariableNames: ''
	classVariableNames: ''
	package: 'Traits-Example'
foo := Foo new.
foo whoAmI == foo
>>> true
	instanceVariableNames: 'count'
	package: 'Traits-Example'
	count := 0
	count := count + 1.
	^ count
	uses: TCounting
	instanceVariableNames: ''
	classVariableNames: ''
	package: 'Traits-Example'
	self initializeTCounting
>>> 2
	uses: {}
	package: 'Traits-Example'
	^ 'I''m speaking!'
	instanceVariableNames: ''
	package: 'Traits-Example'
	^ 'I''m flying'
	uses: TFlyingAbility + TSpeakingAbility 
	instanceVariableNames: ''
	classVariableNames: ''
	package: 'Traits-Example'
d := Duck new.
d speak
>>> 'I''m speaking!'
d fly
>>> 'I''m flying!'
	^ 'QUACK'
	^ self quack
>>> 'QUACK'
	^ 'I double: ', self speak, ' ', self speak
>>> 'I double: QUACK QUACK'
	uses: TFlyingAbility + TSpeakingAbility @{#originalSpeak -> #speak}
	instanceVariableNames: ''
	classVariableNames: ''
	package: 'Traits-Example'
	^ self originalSpeak, ' ', self speak
>>> 'I''m speaking! QUACK'
	instanceVariableNames: ''
	package: 'Traits-Example'
	^ 'I''m flying high'
	uses: THighFlyingAbility + TFlyingAbility 
	instanceVariableNames: ''
	classVariableNames: ''
	package: 'Traits-Example'
>>> 'A class or trait does not properly resolve a conflict between multiple traits it uses.'
	uses: THighFlyingAbility + (TFlyingAbility - #fly)
	instanceVariableNames: ''
	classVariableNames: ''
	package: 'Traits-Example'
>>> 'I''m flying high'
	uses: THighFlyingAbility + TFlyingAbility
	instanceVariableNames: ''
	classVariableNames: ''
	package: 'Traits-Example'
	^ 'Flying and flying high'
>>> 'Flying and flying high'