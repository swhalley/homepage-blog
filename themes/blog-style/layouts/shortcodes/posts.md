{{ with .Get 0 }}
    <fieldset>
        <legend class="font-medium underlined margin-bottom-small">Recent Posts</legend>
        <ul class="posts">
            {{ range first . (where $.Site.Pages "Section" "post") }}
                {{ if .IsPage }}
                    <li>
                        <a href="{{ .Permalink }}" class="clean-link font-grey">{{ .Title }}</a>
                        <span>{{ .Date.Format "2006-01-02" }}</span>
                    </li>
                {{ end }}
            {{ end }}
        </ul>
    </fieldset>
{{ else }}
    <ul class="posts">
    {{ range where $.Site.Pages "Section" "post" }}
        {{ if .IsPage }}
            <li>
                <a href="{{ .Permalink }}" class="font-medium clean-link font-grey">{{ .Title }}</a>
                <span>{{ .Date.Format "2006-01-02" }}</span>
                {{ with .Description }} - {{ end }}
                <span>{{ .Description }}</span>
            </li>
        {{ end }}
    {{ end }}
    </ul>
{{ end }}