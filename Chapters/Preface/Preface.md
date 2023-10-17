## About this book
>>> 7 "if you select 3+4 and 'print it', you will see 7"
    | full empty |
    full := Set with: 5 with: 6.
    empty := Set new.
    self assert: (full includes: 5).
    self assert: (full includes: 6).
    self assert: (empty includes: 5) not
    | full empty |
    full := Set with: 5 with: 6.
    empty := Set new.
    self assert: (full includes: 5).
    self assert: (full includes: 6).
    self assert: (empty includes: 5) not