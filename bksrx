#!/usr/bin/env sh

# bksrx: Firefox bookmark searcher
# LICENSE GPL3

# made with buku, fzf, awk and sed
# tested with:
# fzf 0.27.0 https://github.com/junegunn/fzf
# buku 4.5 https://github.com/jarun/buku
# macos sed, awk and xargs big sur versions

# for awk columns reorder explanation: awk -v OFS='\t' '{print $1, $3, $2}'|\
# see: https://stackoverflow.com/questions/18946434/reordering-columns-with-awk

# for awk column alignment explanation: awk '{printf("%-4s %-70s %s\n", $1, $2, $3)}' |\
# see: https://unix.stackexchange.com/questions/391458/how-to-align-fields-with-printf

# for sed regex explanation: sed 's/^.*http/http/'
# see: https://www.unix.com/unix-for-dummies-questions-and-answers/98893-how-delete-all-character-before-certain-word.html

url=$(buku -p -f2 |
	awk -v OFS='\t' '{print $1, $3, $2}' |
	awk '{printf("%-4s %-70s %s\n", $1, $2, $3)}' |
	fzf -m --layout reverse --info inline --border \
		--preview "buku -p {1}" --preview-window up,8,wrap |
	sed 's/^.*http/http/')

if [ -n "$url" ]; then
	echo "$url" | xargs open -a firefox
fi

# function sync() {

# TODO: sync function
# if pgrep firefox returns 1 DO NOT sync
# if returns 0 DO SYNC sql database with
# boku -ai

# }

# function search_coverage() {
# TODO: search_coverage function
# apply to: url and tag , tag only
# Search applies only to --nth column (tag col: --nth 2)
#}
