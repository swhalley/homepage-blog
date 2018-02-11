<article class='{{ with .Get "className" }}{{ . }}{{ end }} about'>
    <img src="{{ .Site.BaseURL }}{{ .Site.Params.image }}" class="wrap-left" />
    {{ range .Site.Params.about }}
    <p>
        {{ . }}
    </p>
    {{ end }}

    {{ if .Page.IsHome }}{{ else }}
        {{ range .Site.Params.about_ext }}
        <p>
            {{ . }}
        </p>
        {{ end }}
    {{end}}

    <p>{{ .Site.Params.about_thanks }}</p>
    <p class="signature font-biggest">
    {{ .Site.Params.Author}}
</p>
</article>