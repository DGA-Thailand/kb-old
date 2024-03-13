### Welcome to kb.dga.or.th

This is the repo for the kb.dga.or.th website, a resource for DGA products and services' technical documentation, as well as, information, user manuals, and frequently asked questions.

### How to contribute

Please contact the repo's admin to grant you the necessary access.

### How to make changes to the website

- Use https://dga-kb.netlify.app/admin to add, edit contents.
- Or you may set up your local environment.

### Setting Up Local Environment

1. Install Hugo on your computer : https://gohugo.io/installation/
2. Install git on your computer.
3. Clone this repo.
4. Run the following commands:

```bash
cd kb
git init
git submodule init
git submodule update
hugo server
```

or, if you wish to build drafts too. 

```
hugo server -D
```

5. Go to http://localhost:1313.

### Content Structure

- Directory "/content/docs" contains most of webpages, organized by products and services.
- Directory "/static/files" contains files and media used by webpages.
- Refer to decapcms.org documentation for "/static/admin/config.yml"
