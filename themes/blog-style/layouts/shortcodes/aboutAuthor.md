<article class='{{ with .Get "className" }}{{ . }}{{ end }} about'>
    <img src="{{ .Site.BaseURL }}/{{ .Site.Params.image }}" class="wrap-left" />
    {{ range .Site.Params.about }}
    <p>
        {{ . }}
    </p>
    {{ end }}
    <p class="signature font-biggest">
    {{ .Site.Params.Author}}
    </p>
</article>