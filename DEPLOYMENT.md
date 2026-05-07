# KarFlows Docs Deployment

KarFlows docs can be deployed in two professional ways.

## Best Option: `docs.your-domain.com`

This is the easiest and safest path.

1. Push the `docs` folder to GitHub.
2. Create a Mintlify project.
3. Point Mintlify to the `docs` folder.
4. In Mintlify, add the custom domain:

   ```text
   docs.your-domain.com
   ```

5. In DNS, create the CNAME record Mintlify gives you.

Use this when you want docs to deploy separately from the KarFlows SaaS app.

## Main Domain Option: `your-domain.com/docs`

This is possible, but it needs a subpath proxy.

Mintlify-hosted docs do not simply work by copying the `docs` folder into `client/public/docs`. The `.mdx` files need a docs renderer.

Use one of these:

- Cloudflare Worker reverse proxy from `your-domain.com/docs/*` to the Mintlify docs host.
- Vercel rewrites if the main app is in Vercel.
- Apache/Nginx reverse proxy if the host allows proxy rules.
- Convert the docs to a static Docusaurus/Redocly site and build into `client/public/docs`.

For cPanel shared hosting, `docs.your-domain.com` is usually cleaner than `/docs` because many shared hosts do not allow reverse proxy modules.

## Local Preview

From Windows PowerShell:

```powershell
cd C:\laragon\www\Karflow\docs
npx mint dev
```

Open:

```text
http://localhost:3000
```

Stop the preview with:

```text
Ctrl + C
```

If `npx mint dev` asks to install the package, type `y`.

## Dark Mode And White Mode

The docs theme is configured in:

```text
docs/mint.json
```

KarFlows colors:

```json
{
  "primary": "#00A884",
  "light": "#E6F7F3",
  "dark": "#071314"
}
```

Mintlify handles light/dark mode rendering. Keep code blocks, tables, and callouts in MDX components instead of custom hardcoded HTML so both modes stay clean.

## Domain Changes

If the app domain changes, update:

```text
docs/mint.json
docs/openapi/karflows.yaml
```

Then search docs for the old domain:

```powershell
Select-String -Path .\**\*.mdx,.\**\*.yaml -Pattern "old-domain.com"
```
