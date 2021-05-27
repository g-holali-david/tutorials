%title: Helm
%author: xavki
%Vidéos: [Helm]()
%blog: [Xavki Blog](https://xavki.blog)

# HELM : La Force de Helm démo !!!

<br>

```
{{- define "mychart.mylabels" -}}
labels:
  env: {{ .Values.env }}
  app: {{ .Release.Name }}
{{- end }}
```


```
{{- define "mychart.mylabels" -}}
name: {{ .Release.Name }}
labels:
  env: {{ .Values.env }}
  app: {{ .Release.Name }}
{{- end }}
```

```
metadata:
{{ include "mychart.mylabels" . | indent 2}}
```
