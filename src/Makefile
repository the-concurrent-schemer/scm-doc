HTML = $(patsubst %.asciidoc,%.html,$(shell find . -depth 1 -name \*.asciidoc))
PDF = $(patsubst %.asciidoc,%.pdf,$(shell find . -depth 1 -name \*.asciidoc))

all: html

html: $(HTML)

pdf: $(PDF)

clean:
	rm -f $(HTML) $(PDF)

%.html: %.asciidoc Makefile
	cd $(<D) && asciidoc -b bootstrap-docs -a data-uri -a icons -a toc2 $(<F)

%.pdf: %.asciidoc Makefile
	cd $(<D) && a2x -f pdf $(<F)

.PHONY: all html pdf clean
