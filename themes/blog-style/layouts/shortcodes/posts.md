<ul>
    {{ with .Get 0 }}
        {{ range first . (where $.Site.Pages "Section" "post") }}
            {{ if .IsPage }}
                <li><a href="{{ .Permalink }}">{{ .Title }}</a></li>
            {{ end }}
        {{ end }}
    {{ else }}
        {{ range where .Site.Pages "Section" "post" }}
            {{ if .IsPage }}
                <li><a href="{{ .Permalink }}">{{ .Title }}</a></li>
            {{ end }}
        {{ end }}
    {{ end }}
</ul>