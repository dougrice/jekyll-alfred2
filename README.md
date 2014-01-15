jekyll-alfred2
==============

**Create [Jekyll](http://jekyllrb.com/) static pages & execute Jekyll-related commands using [Alfred](http://www.alfredapp.com/)**

### Keyword → post

Takes text entered following keyword **post** (no hyphens required) and creates a properly named [Markdown](http://daringfireball.net/projects/markdown/) file in the `_posts` directory. The file is then opened in [Byword](http://bywordapp.com/) for editing: `2014-01-14-this-is-a-post.md`

```
file=$(echo "$( date '+%Y-%m-%d-' ){query}.md" | tr " " "-")
touch ~/path/to/jekyll/"$file" && open -a "Byword" ~/path/to/jekyll/"$file"
```

### Keyword → draft

Takes text entered following keyword **draft** (no hyphens required) and creates a properly named [Markdown](http://daringfireball.net/projects/markdown/) file in the `_drafts` directory. The file is then opened in [Byword](http://bywordapp.com/) for editing: `this-is-a-draft.md`

```
file=$(echo "{query}.md" | tr " " "-")
touch ~/path/to/jekyll/_drafts/"$file" && open -a "Byword" ~/path/to/jekyll/_drafts/"$file"
```

### Keyword → page

Takes text entered following keyword **page** (no hyphens required) and creates a properly named [Markdown](http://daringfireball.net/projects/markdown/) file in the `root` directory. The file is then opened in [Byword](http://bywordapp.com/) for editing: `page.md`

```
file=$(echo "{query}.md" | tr " " "-")
touch ~/path/to/jekyll/"$file" && open -a "Byword" ~/path/to/jekyll/"$file"
```

### Keyword → watch

Applescript that runs `jekyll serve --watch` in Terminal also minimizing the window:


```applescript
tell application "Terminal"
	set miniaturized of window 1 to true
	do script "cd /Users/doug/ut && jekyll serve --watch && exit"
end tell
```

### Keyword → publish

Applescript that runs `jekyll build` in Terminal. The pages are published via `rsync`:

```applescript
tell application "Terminal"
	activate
	do script "cd /path/to/jekyll && jekyll build && rsync -v -crz --delete _site/ -e 'ssh -p 2222' name@domain.com:/home/public_html/ && exit"
end tell
```

## Download Alfred workflow

