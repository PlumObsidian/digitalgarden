---
{"dg-publish":true,"permalink":"/software/hugo/rsync-shell-script-for-a-hugo-deploy/","tags":["hugo"]}
---

```bash
nano deploy
```

``` bash
#!/bin/sh

hugo && rsync -avz --delete public/ <user>@,server>:/var/www/<your
_doc_root>

exit 0
```

```bash
chmod a+x deploy
```

Now to deploy from Hugo site root:

```bash
./deploy
```

Simplistic but you can also set user and server as variables if that's preferred.