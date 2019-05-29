SHELL = /bin/sh

targets = $(patsubst %.md, bin/%.pdf, $(wildcard *.md))

latex_template = https://raw.githubusercontent.com/Wandmalfarbe/pandoc-latex-template/master/eisvogel.tex

.PHONY: all
all: installdirs main

.PHONY: installdirs
installdirs: 
	@ mkdir -p bin 

.PHONY: clean
clean:
	rm -f bin/*

main: $(targets)

bin/%.pdf: %.md
	pandoc -t latex --pdf-engine xelatex -f markdown_github+raw_tex+superscript+escaped_line_breaks+tex_math_dollars+yaml_metadata_block --listings --template $(latex_template) -o $@ $<
