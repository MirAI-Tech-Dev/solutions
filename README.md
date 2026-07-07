# solutions
Page Forward

## `index.html`

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>MirAI Tech Solutions</title>
    <meta http-equiv="refresh" content="0; url=https://miraitech.dev/" />
    <link rel="canonical" href="https://miraitech.dev/" />
  </head>
  <body>
    <p>
      Redirecting to <a href="https://miraitech.dev/">https://miraitech.dev/</a>...
    </p>
  </body>
</html>
```

## `404.html`

GitHub Pages cannot emit real HTTP 301 redirects (it serves static files only
— no `.htaccess`, `_redirects`, or server config). This page is the closest
equivalent: a 0-second meta refresh (treated by search engines as
301-equivalent), a canonical link, and a JS `location.replace()` fallback, all
preserving the original path/query/hash.

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>Redirecting...</title>
    <!--
      GitHub Pages cannot emit real HTTP 301 redirects (static-only hosting).
      This page is the closest equivalent: a 0-second meta refresh (treated by
      search engines as 301-equivalent) plus a canonical link and a JS
      location.replace() fallback, all preserving the original path/query/hash.
    -->
    <script>
      (function () {
        var path = window.location.pathname || "/";
        var query = window.location.search || "";
        var hash = window.location.hash || "";
        var dest = "https://miraitech.dev" + path + query + hash;

        // 301-equivalent signals for crawlers
        var meta = document.createElement("meta");
        meta.httpEquiv = "refresh";
        meta.content = "0; url=" + dest;
        document.head.appendChild(meta);

        var link = document.createElement("link");
        link.rel = "canonical";
        link.href = dest;
        document.head.appendChild(link);

        // Immediate redirect for browsers (no history entry, like a 301)
        window.location.replace(dest);
      })();
    </script>
  </head>
  <body>
    <p>
      This page has moved to
      <a id="manual-link" href="https://miraitech.dev/">https://miraitech.dev/</a>.
    </p>
  </body>
</html>
```

## Step-by-step terminal commands

```bash
mkdir <repo-name>
cd <repo-name>
git init

cat > index.html <<'HTML'
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>MirAI Tech Solutions</title>
    <meta http-equiv="refresh" content="0; url=https://miraitech.dev/" />
    <link rel="canonical" href="https://miraitech.dev/" />
  </head>
  <body>
    <p>
      Redirecting to <a href="https://miraitech.dev/">https://miraitech.dev/</a>...
    </p>
  </body>
</html>
HTML

cat > 404.html <<'HTML'
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>Redirecting...</title>
    <!--
      GitHub Pages cannot emit real HTTP 301 redirects (static-only hosting).
      This page is the closest equivalent: a 0-second meta refresh (treated by
      search engines as 301-equivalent) plus a canonical link and a JS
      location.replace() fallback, all preserving the original path/query/hash.
    -->
    <script>
      (function () {
        var path = window.location.pathname || "/";
        var query = window.location.search || "";
        var hash = window.location.hash || "";
        var dest = "https://miraitech.dev" + path + query + hash;

        // 301-equivalent signals for crawlers
        var meta = document.createElement("meta");
        meta.httpEquiv = "refresh";
        meta.content = "0; url=" + dest;
        document.head.appendChild(meta);

        var link = document.createElement("link");
        link.rel = "canonical";
        link.href = dest;
        document.head.appendChild(link);

        // Immediate redirect for browsers (no history entry, like a 301)
        window.location.replace(dest);
      })();
    </script>
  </head>
  <body>
    <p>
      This page has moved to
      <a id="manual-link" href="https://miraitech.dev/">https://miraitech.dev/</a>.
    </p>
  </body>
</html>
HTML

git add index.html 404.html
git commit -m "Set up GitHub Pages global redirects to miraitech.dev"
git branch -M main
git remote add origin git@github.com:<your-username>/<repo-name>.git
git push -u origin main
```

This setup redirects:
- Root: `https://miraitech.solutions/` -> `https://miraitech.dev/`
- Deep links: `https://miraitech.solutions/portfolio/` -> `https://miraitech.dev/portfolio/`
