HTML = $(patsubst %.asciidoc,%.html,$(shell find . -depth 1 -name \*.asciidoc))
PDF = $(patsubst %.asciidoc,%.pdf,$(shell find . -depth 1 -name \*.asciidoc))

all: html

html: $(HTML)

pdf: $(PDF)

gh-pages: clean html
	git co gh-pages
	rsync -avz ./index.html ../index.html
	rsync -avz ./contributors.html ../contributors.html
	rsync -avz --exclude=.git --delete ./bootstrap-docs/bootstrap/ ../bootstrap/

clean:
	rm -f $(HTML) $(PDF)

%.html: %.asciidoc Makefile
	cd $(<D) && asciidoc $(<F)
	@perl -i -pe 's~class="brand" href="#"~class="brand" href="https://github.com/the-concurrent-schemer"~;' $(@)
	@perl -i -pe 's~rel="shortcut icon" href="./bootstrap/docs/assets/ico/favicon.ico"~rel="shortcut icon" href="http://www.gravatar.com/avatar/4b50e81570fd42f2d9a43c87f8c19456.png"~;' $(@)

%.pdf: %.asciidoc Makefile
	cd $(<D) && a2x -f pdf $(<F)

.PHONY: all html pdf clean
