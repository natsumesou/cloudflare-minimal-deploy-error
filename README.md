# Cloudflare Workers AI Binding Deployment Error

This repository is a minimal reproduction of a Cloudflare Workers deployment failure when a Workers AI binding is added.

The same Worker deploys successfully without the binding, but fails with Cloudflare error `10021` when only the `WORKERS_AI` binding is added.

## Reproduction

Deploy without the Workers AI binding:

```bash
npx wrangler@4.141.0 deploy --config wrangler.base.jsonc
```

This succeeds.

Then deploy the same Worker with the Workers AI binding:

```bash
npx wrangler@4.141.0 deploy --config wrangler.ai.jsonc
```

This fails with:

```text
binding WORKERS_AI of type ai failed to generate:
internal error; please try again later or contact support:
unknown error, please try again later or contact the support [code: 10021]
```

Removing the binding and deploying with `wrangler.base.jsonc` succeeds again.
