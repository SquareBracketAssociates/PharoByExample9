## Regular expressions in Pharo
>>> true
>>> true
>>> true
>>> false
>>> false
	webDir := dir.
	homePath := path

WebDir class >> onDir: dir
	^ self new setDir: dir home: dir pathString

WebDir class >> selectHome
	^ self onDir: UIManager default chooseDirectory
	^ self onPath: homePath home: homePath

WebDir class>>onPath: path home: homePath
	^ self new setDir: path asFileReference home: homePath
>>> true
>>> true
>>> true
>>> true
>>> true
>>> true
>>> false
>>> true
>>> true
>>> true
>>> false
>>> true
>>> true
>>> false
>>> false
	^ webDir fileNames select: [ :each | each matchesRegex: '.*\.html' ]
>>> #('index.html' ...)
	htmlRegex := '.*\.html' asRegex

WebDir >> htmlFiles
	^ webDir fileNames select: [ :each | htmlRegex matches: each ]
	path := filePath.
	homePath := dirPath

WebPage class >> on: filePath forHome: homePath
	^ self new initializePath: filePath homePath: homePath
	^ self htmlFiles collect:
		[ :each | WebPage
			on: webDir pathString, '/', each
			forHome: homePath ]
>>> an Array(a WebPage a WebPage ...)
>>> 'hi'
	^ path copyWithRegex: '.*/' matchesReplacedWith: ''
>>> #('index.html' ...)
	^ (ZnCharacterReadStream on: (File named: path) readStream encoding: 'utf8') contents
>>> '<!DOCTYPE HTML>
<html>
<head>
...
'
re := '([CARETaeiou]+)([aeiou]+)' asRegex.
re matchesPrefix: 'pharo'
>>> true
>>> 'pha'
>>> 'ph'
>>> 'a'
	| re |
	re := '[\w\W]*<title>(.*)</title>' asRegexIgnoringCase.
	^ (re matchesPrefix: self contents)
		ifTrue: [ re subexpression: 2 ]
		ifFalse: [ '(', self fileName, ' -- untitled)' ]
newlines_. \(If we expect titles to possible contain newlines, we should play
>>> 'Home page'
>>> '/index.html'
>>>  'index.html'
	^ path
		copyWithRegex: homePath, '/'
		matchesReplacedWith: ''

WebPage >> link
	^ '<a href="', self relativePath, '">', self title, '</a>'
>>> '<a href="index.html">Home Page</a>'
	^ webDir directoryNames
		collect: [ :each | WebDir onPath: webDir pathString, '/', each home: homePath ]
	self htmlFiles
		ifNotEmpty: [
			aStream nextPutAll: '<ul>'; cr.
			self webPages
				do: [:each | aStream nextPutAll: '<li>';
						 nextPutAll: each link;
						 nextPutAll: '</li>'; cr].
			self webDirs
				do: [:each | each printTocOn: aStream].
			aStream nextPutAll: '</ul>'; cr]
	^ 'toc.html'

WebDir >> makeToc
	| tocStream |
	tocStream := (webDir / self tocFileName) writeStream.
	self printTocOn: tocStream.
	tocStream close.
>>> true
>>> true
>>> false
>>> true
>>> true
>>> true
>>> false    "b does not match"
occurrences of `ab`_:
>>> true
>>> false
>>> true
>>> false    "c spoils the fun"
>>> true
>>> false    "need at least one b"
>>> true
>>> false    "too many b's"
>>> false    "star in the right string is special"
>>> true
>>> true
number of a's_:
>>> true
>>> true
>>> false
>>> true
>>> true
>>> true
>>> true
>>> false
>>> false  "a set matches only one character"
>>> true
>>> false
>>> false
>>> true
>>> true    "put the caret anywhere except the start"
>>> true    "put the hyphen at the end"
>>> true    "put the closing bracket at the start"
>>> true
>>> false
>>> true
>>> true
>>> true
>>> false    "leading 0"
>>> true
>>> true
>>> true
>>> true
>>> false    "negative zero"
>>> false    "leading zero"
>>> true
>>> true
>>> true
>>> true
>>> false    "need digits after ."
>>> true
>>> true
>>> true
>>> true
>>> true
>>> true
>>> true
>>> true      "word boundary before w"
>>> false    "no boundary before o"
>>> false
>>> true
>>> true
>>> false
>>> true
list := OrderedCollection new.
'Jack meet Jill' regex: '\w+' matchesDo: [:word | list add: word].
list
>>> an OrderedCollection('Jack' 'meet' 'Jill')
>>> an OrderedCollection(4 4 4)
>>> an OrderedCollection('Jack' 'and' 'Jill' 'went' 'up' 'the' 'hill')
>>> 'Krazy loves Ignatz'
>>> 'Krazy LOVES Ignatz'
octal := '8r[0-9A-F]+' asRegex.
octal matchesIn: '8r52 = 16r2A'
>>> an OrderedCollection('8r52')
hex := '16r[0-9A-F]+' asRegexIgnoringCase.
hex matchesIn: '8r52 = 16r2A'
>>> an OrderedCollection('16r2A')
hex := RxMatcher forString: '16r[0-9A-Fa-f]+' ignoreCase: true.
hex matchesIn: '8r52 = 16r2A'
>>> an OrderedCollection('16r2A')
>>> true
>>> true
>>> true    "finds 'hates'"
number := '\d+' asRegex.
number search: 'Ignatz throws 5 bricks'.
number lastResult
>>> true
ignatz := ReadStream on: 'Ignatz throws bricks at Krazy'.
names := '\<[A-Z][a-z]+\>' asRegex.
names matchesStreamPrefix: ignatz
>>> true
2:    (\d+)\s*(\w+)       "top parenthesized subexpression"
3:    \d+                      "first leaf subexpression"
4:    \w+                     "second leaf subexpression"
items := '((\d+)\s*(\w+))' asRegex.
items search: 'Ignatz throws 1 brick at Krazy'.
items subexpressionCount
>>> 4
>>> '1 brick'    "complete expression"
>>> '1 brick'    "top subexpression"
>>> '1'             "first leaf subexpression"
>>> 'brick'       "second leaf subexpression"
>>> an OrderedCollection(14)
>>> an OrderedCollection(15)
>>> an OrderedCollection(16)
>>> an OrderedCollection(21)
date := '(Jan|Feb|Mar|Apr|May|Jun|Jul|Aug|Sep|Oct|Nov|Dec)\s+(\d\d?)\s*,\s*19(\d\d)' asRegex.
result := (date matches: 'Aug 6, 1996')
       ifTrue: [{ (date subexpression: 4) .
				(date subexpression: 2) .
				(date subexpression: 3) } ]
        ifFalse: ['no match'].
result
>>> #('96' 'Aug' '6')
seuss := 'The cat in the hat is back'.
aWords := '\<([^aeiou]|[a])+\>' asRegex.    "match words with 'a' in them"
aWords matchesIn: seuss
>>> an OrderedCollection('cat' 'hat' 'back')
>>> an OrderedCollection('CAT' 'HAT' 'BACK')
>>> 'The grinch in the grinch is grinch'
>>> 'The CAT in the HAT is BACK'
>>> 'RegexSyntaxError:  nullable closure'