# Automatic jupyter books 

Jupyter book is a 'static html' rendering tool to create a website from markdown and jupyter notebooks. Here's a quick summary of how to use it to first create a local html website on your computer and then how to use git and github actions to quickly build or post updates to the site on the web using github pages. 

1. `pip install jupyter-book`
2. clone** the repo at `https://github.com/jhconning/jbook`  (you can change the name later)
3. Create new markdown (.md) and/or jupyter notebook (.ipynb) files (I've placed them in the `notes` folder but you can put them anywhere). 
3. Edit the `_toc.yml` file to include your pages. TOC details [here](https://jupyterbook.org/en/stable/structure/toc.html).  This establishes the navigation bar for your website.
The `_config.yml` lets you change websitetitle, logo, and theme.  Details [here](https://jupyterbook.org/en/stable/customize/config.html).
4. To see how the build will look locally, from a command line type: `jb build .` 
   This will create a `_build` folder with the html rendered files.  Open the `index.html` file in a browser to see the website.  
5. With the github action workflow (setup with the file at `.github/workflows/book.html`), any new git push to the remote repository will tell github to create a virtual machine that will install jupyterbook and build your website from the files pushed to the repo.  For this to happen you need to setup github to build github pages and respond to your actions.
  - On your github repo 
      - `settings/Actions/General` set workflow permissions to 'read and write'.  
      - `settings/Pages` set source to `gh-pages` branch, folder to `/root`.  and 'deploy from branch'.



** Aalternatively at step 2 type `jupyter-book create mybook` to create an entirely new book, but you'll need to `.github/workflows/book.html` to get the github actions part to work.



