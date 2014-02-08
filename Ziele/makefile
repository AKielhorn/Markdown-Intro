# Makefile for pandoc 1.10
# --no-tex-ligatures ab pandoc 1.9.3
PANDOC=~/.cabal/bin/pandoc
DOC=md-test
QUELLEN=$(DOC).md $(DOC).bib blau.jpg rot.png cover-image.gif
KINDLEGEN=/Applications/Texte/KindleGen/kindlegen

all: html txt pdf epub odt docx

html:	$(DOC).html

txt:	$(DOC).txt

tex:	$(DOC).tex

pdf:	$(DOC).pdf

epub:	$(DOC).epub

odt:	$(DOC).odt

docx:	$(DOC).docx

mobi:	$(DOC).mobi

kindle:	$(DOC).mobi

$(DOC).html: 	$(QUELLEN) makefile
	$(PANDOC) -f markdown $(DOC).md -s --toc --bibliography $(DOC).bib -o $(DOC).html

$(DOC).txt:	$(QUELLEN)
	$(PANDOC) -f markdown -t plain -s $(DOC).md --bibliography $(DOC).bib -o $(DOC).txt

$(DOC).tex:	$(DOC).md $(DOC).bib default-de-1.12.latex
	$(PANDOC) -f markdown $*.md -t latex -V documentclass=article --no-tex-ligatures -S --template=./default-de-1.12.latex --bibliography $*.bib --biblatex -o $*.tex
#	Für Pandoc 1.9 anderes Template verwenden
#	$(PANDOC) -f markdown $*.md -t latex -V documentclass=article --no-tex-ligatures -S --template=./default-de-1.9.latex --bibliography $*.bib --biblatex -o $*.tex
#	Standard pandoc template
#	$(PANDOC) -f markdown $*.md -t latex -V documentclass=article -V lang=ngerman --no-tex-ligatures -S -s --bibliography $*.bib --biblatex -o $*.tex

$(DOC).pdf:	$(DOC).md $(DOC).bib default-de-1.12.latex
	$(PANDOC) $(DOC).md --filter pandoc-citeproc --no-tex-ligatures --template=./default-de-1.12.latex -o $(DOC).pdf

$(DOC).epub:	$(QUELLEN)
	$(PANDOC) -f markdown $(DOC).md --toc --epub-cover-image=cover-image.gif -V lang=de_DE -s --bibliography $(DOC).bib -o $(DOC).epub

$(DOC).odt: $(QUELLEN) reference-de.odt
	$(PANDOC) -f markdown -t odt --reference-odt=./reference-de.odt -s --bibliography $(DOC).bib -o $(DOC).odt $(DOC).md

$(DOC).docx: $(QUELLEN) reference-de.docx
	$(PANDOC) -f markdown -t odt --reference-docx=./reference-de.docx -s --bibliography $(DOC).bib -o $(DOC).docx $(DOC).md

# Erfordert kindlegen von amazon.com
# Erfordert pandoc >= 1.9
$(DOC).mobi:	$(DOC).epub
	$(KINDLEGEN) $(DOC).epub

# Alternativ:
# Erfordert Kommandozeilen Werkzeuge aus calibre
# ebook-convert $(DOC).epub $(DOC).mobi --output-profile=kindle

clean:
	rm $(DOC).aux
	rm $(DOC).bbl
	rm $(DOC).blg
	rm $(DOC).fdb_latexmk
	rm $(DOC).log
	rm $(DOC).out
	rm $(DOC).run.xml
	rm $(DOC)-blx.bib

distclean:
	rm $(DOC).aux
	rm $(DOC).bbl
	rm $(DOC).blg
	rm $(DOC).fdb_latexmk
	rm $(DOC).log
	rm $(DOC).out
	rm $(DOC).run.xml
	rm $(DOC).html
	rm $(DOC).txt
	rm $(DOC).pdf
	rm $(DOC).tex
	rm $(DOC).epub
	rm $(DOC).odt


# pandoc -f markdown -t latex -o Ziele-md.tex --no-tex-ligatures -S --template=Ziele-md.latex --bibliography Ziele-md.bib --csl=Ziele.csl Ziele-md.md 

