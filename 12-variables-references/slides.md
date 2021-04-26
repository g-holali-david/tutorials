%title: Helm
%author: xavki
%Vidéos: [Helm]()
%blog: [Xavki Blog](https://xavki.blog)

# HELM : VARIABLES DE REFERENCES



<br>

* différents objets :

		* release

		* values

		* chart

		* files

		* capabilities

		* template

Cf : https://helm.sh/docs/chart_template_guide/builtin_objects/


-----------------------------------------------------------------

# HELM : VARIABLES DE REFERENCES


<br>

RELEASE

	* .Release.Name

	* .Release.Namespace

	* .Release.IsUpgrade

	* .Release.IsInstall

	* .Release.Revision

	* .Release.Service

-----------------------------------------------------------------

# HELM : VARIABLES DE REFERENCES

<br>

VALUES

	* cf le fichier de values

<br>

CHART

	* .Chart.Name

	* .Chart.Version

	* .Chart.AppVersion

	* .Chart.Description

-----------------------------------------------------------------

# HELM : VARIABLES DE REFERENCES

<br>

FILES

	* .Files.Get "monfichier.txt" : récupérer un fichier par son nom

	* .Files.GetBytes : récupérer le contenu de fichier sous forme de bytes

	* .Files.Glob : liste de fichier selon un pattern

```
{{ .Files.Glob "files/xavk`*.txt".AsConfig}}
```

	* .Files.Lines "path" : pour lire un fichier ligne par ligne

	* .Files.AsSecrets : converti le contenu en base64

```
{{ (.Files.Glob "files/xavk*.txt").AsConfig | indent 2}}
```

	* .Files.AsConfig : converti en format yaml


-----------------------------------------------------------------

# HELM : VARIABLES DE REFERENCES

<br>

CAPABILITIES

	* .Capabilities.APIVersions

	* .Capabilities.KubeVersion

	* .Capabilities.KubeVersion.Major

	* .Capabilities.KubeVersion.Minor

<br>

TEMPLATES

	* .Template.Name

	* .Template.BasePath
