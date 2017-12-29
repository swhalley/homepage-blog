<ul class="posts">
    {{ with .Get 0 }}
        {{ range first . (where $.Site.Pages "Section" "post") }}
            {{ if .IsPage }}
                <li>
                    <a href="{{ .Permalink }}" class="font-medium">{{ .Title }}</a>
                    <span>{{ .Date.Format "2006-01-02" }}</a>
                </li>
            {{ end }}
        {{ end }}
    {{ else }}
        {{ range where $.Site.Pages "Section" "post" }}
            {{ if .IsPage }}
                <li>
                    <a href="{{ .Permalink }}" class="font-medium">{{ .Title }}</a>
                    <span>{{ .Date.Format "2006-01-02" }}</a>
                </li>
            {{ end }}
        {{ end }}
    {{ end }}
</ul>