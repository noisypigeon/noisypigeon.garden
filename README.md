# noisypigeon.garden

**This repo is empty on purpose.** It only deploys
[noisypigeon.garden](https://noisypigeon.garden), the short-URL host for the
Terraform modules in [`noisypigeon/library`](https://github.com/noisypigeon/library):

```hcl
source = "https://noisypigeon.garden/terraform/<provider>/<module>/vX.Y.Z"
```

The site's source lives in
[`noisypigeon/runway`](https://github.com/noisypigeon/runway), at
[`workloads/garden/`](https://github.com/noisypigeon/runway/tree/main/workloads/garden):
its Zola site, its generated module pages and schemas, and the DNS of the zone
it owns. runway's `garden-generate.yml` regenerates those pages, and the
library dispatches it on every release.

GitHub Pages only deploys the repository a workflow runs in, and each site has
one custom domain. So noisypigeon.garden needs a repository of its own, and this
is it: one workflow, [`pages.yml`](.github/workflows/pages.yml), that builds
runway's `main` and deploys it here. runway dispatches it whenever the site
changes, by the shim its `values.yaml` names
([LIB-0031](https://github.com/noisypigeon/library/blob/main/docs/adr/LIB-0031-site-workloads-and-pages-shim-repos.md),
[LIB-0034](https://github.com/noisypigeon/library/blob/main/docs/adr/LIB-0034-site-workloads-declare-their-pages-shim.md),
[LIB-0035](https://github.com/noisypigeon/library/blob/main/docs/adr/LIB-0035-move-garden-into-runway.md)).
