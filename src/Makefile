# Makefile for generating and installing PCF font files

whereto = /usr/share/fonts/X11/misc # arg to the install target
# Other reasonable destinations:
# $(HOME)/.local/share/fonts
# $(HOME)/.fonts
# /usr/share/fonts/X11/misc
# See https://github.com/wch/extrafont/issues/52

SHELL=/bin/bash


all: 9x18.pcf.gz 9x18B.pcf.gz

%.pcf.gz:	%.bdf
	bdftopcf $< | gzip -9 > $@

install: 9x18.pcf.gz 9x18B.pcf.gz
	test -e $(whereto) && test -d $(whereto) || mkdir -p $(whereto)
	cp -u $< $(whereto)
	cd $(whereto) ; mkfontdir
	xset +fp $(whereto) # update the font-path for the current session

clean:
	rm -f fonts.dir *.pcf *.gz *~





