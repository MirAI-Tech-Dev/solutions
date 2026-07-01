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

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>Redirecting...</title>
    <script>
      window.getDestinationUrl = function () {
        const path = window.location.pathname || "/";
        const query = window.location.search || "";
        const hash = window.location.hash || "";
        return "https://miraitech.dev" + path + query + hash;
      };

      window.location.replace(window.getDestinationUrl());
    </script>
  </head>
  <body>
    <p>
      This page has moved to
      <a id="manual-link" href="https://miraitech.dev/">https://miraitech.dev/</a>.
    </p>
    <script>
      if (typeof window.getDestinationUrl === "function") {
        document.getElementById("manual-link").href = window.getDestinationUrl();
      }
    </script>
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
    <script>
      window.getDestinationUrl = function () {
        const path = window.location.pathname || "/";
        const query = window.location.search || "";
        const hash = window.location.hash || "";
        return "https://miraitech.dev" + path + query + hash;
      };

      window.location.replace(window.getDestinationUrl());
    </script>
  </head>
  <body>
    <p>
      This page has moved to
      <a id="manual-link" href="https://miraitech.dev/">https://miraitech.dev/</a>.
    </p>
    <script>
      if (typeof window.getDestinationUrl === "function") {
        document.getElementById("manual-link").href = window.getDestinationUrl();
      }
    </script>
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
