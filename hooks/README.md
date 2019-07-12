# Nauta-zoo hooks


## update_gh_pages.py

Does following things:
- Packs all template directories (i.e. directories in repo that have valid Chart.yaml file)
  in tar.gz archives and stores them in /docs directory
- Generates index.json file, which contains metadata of all templates

These steps automates creation and updates of template repository server used by nctl.
Content of docs folder is intended to be hosted using GitHub Pages
(in similar manner to the way how Helm chart repositories are hosted).


This script may be used either manually or as a pre-commit hook.
In order to install it as pre-commit hook, run following command in repos' main directory:
```bash
ln -sf $(pwd)/hooks/update_gh_pages.py .git/hooks/pre-commit
chmod +x .git/hooks/pre-commit
```

## Testing changes in nauta-zoo templates

In order to test changes made in templates ,for `nctl template list` and `nctl template install` commands,
you can fork this repo and setup GitHub pages in forked
repository (instructions: 
https://help.github.com/en/articles/configuring-a-publishing-source-for-github-pages#publishing-your-github-pages-site-from-a-docs-folder-on-your-master-branch),
and configure nctl to use nauta-zoo hosted on your repository
 (by changing `model-zoo-address` in `$NCTL_CONFIG/zoo-repository.config` to `http://<your_github_username>.github.io/nauta-zoo`).