%title: Helm
%author: xavki
%Vidéos: [Helm]()
%blog: [Xavki Blog](https://xavki.blog)

# HELM : Fonctions 

<br>

PRINT...

print "Matt has " .Dogs " dogs"
printf "%s has %d dogs." .Name .NumberDogs

<br>

TRIM

trim "   hello    "
trimAll "$" "$5.00"
trimPrefix "-" "-hello"
trimSuffix "-" "hello-"


LOWER/UPPER

lower "HELLO"
upper "hello"
title "hello world"


REPEAT

repeat 3 "hello"	



SUBSTRING/TRUNC/INITIALS

substr 0 5 "hello world"
trunc 5 "hello world"
initials "First Try"

NOSPACE

nospace "hello w o r l d"



RAND

randAlphaNum uses 0-9a-zA-Z
randAlpha uses a-zA-Z
randNumeric uses 0-9
randAscii uses all printable ASCII characters

randNumeric 3


CONTAINS/PREFIX

contains "cat" "catch"
hasPrefix "cat" "catch"

CAT

cat "hello" "beautiful" "world"


QUOTE/SQUOTE

quote .Values.var1
squote .Values.var1


INDENT/NINDENT

indent 4 .Values.var1
nindent 4 .Values.var1


REPLACE

"I Am Henry VIII" | replace " " "-"


SNAKECASE/CAMELCASE/KEBABCASE/SWAPCASE

snakecase "FirstName"
camelcase "http_server"
kebabcase "FirstName"
swapcase "This Is A.Test"


SHUFFLE

shuffle "hello"




