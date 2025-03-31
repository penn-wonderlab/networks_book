# About

## To preview

```
jupyter-book build .
```

## Commands for updating course website

```
cd networks_book
jupyter-book clean -a .
jupyter-book build .
git add .
git commit -m "comment"
git push
ghp-import -n -p -f _build/html
```