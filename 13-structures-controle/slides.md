%title: Helm
%author: xavki
%Vidéos: [Helm]()
%blog: [Xavki Blog](https://xavki.blog)

# HELM : CONDITIONS ET OPERATEURS



<br>

IF / ELSE


```
{{ if condition }}
{{ else if condition }}
{{ else }}
{{ end }}
```

Note : condition = true/false

<br>

False :
		* false
		* 0 numérique
		* nil or empty or null
		* collections vides : map, slice, tuple, dict , array


------------------------------------------------------------------------------

# HELM : CONDITIONS ET OPERATEURS


<br>

TESTS LOGIQUES

* retourne des true/false

<br>

* AND : et

```
and .Values.key1 .Values.key2
and (test1) (test2)
{{ if and (test1) (test2) }}
```

<br>

* OR : ou

```
or .Values.key1 .Values.key2
or (test1) (test2)
```

------------------------------------------------------------------------------

# HELM : CONDITIONS ET OPERATEURS

<br>

* NOT : négation

```
not .Values.key1
not (test1)
```

<br>

* EQ : compare deux variables/formules

```
eq .Values.key1
eq (test1)
```

<br>

* NE : non égale

```
ne .Values.key1
ne (test1)
```

------------------------------------------------------------------------------

# HELM : CONDITIONS ET OPERATEURS


<br>

* LT : plus petit que strictement

* LE : plus petit ou égal à

* GT : plus grand 

* GE : plus grand ou égal

------------------------------------------------------------------------------

# HELM : CONDITIONS ET OPERATEURS


<br>

* DEFAULT : si valeur vide set une autre valeur

```
default "valeur par défaut" .Values.key1
```

Note : sont des valeurs vides
		* numérique : 0
		* string : ""
		* liste []
		* dict : {}
		* boolean : false
		* nil ou null

------------------------------------------------------------------------------

# HELM : CONDITIONS ET OPERATEURS

<br>

* EMPTY : retourne true sur valeur vide

```
empty .Values.key1
```

<br>

* FAIL : retourne un texte sous forme d'erreur

fail "Ceci est une erreur"

<br>

* COALESCE : retourne la première valeur non vide d'une liste

```
coalesce 0 1 2
```

<br>

* TERNARY : retourne première valeur sur true sinon seconde

```
ternary "valeur1" "valeur2" (test)
(test) | ternary "valeur1" "valeur2"
```

