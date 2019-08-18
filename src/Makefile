# Makefile for generating and installing PCF font files

whereto = /usr/share/fonts/X11/misc # arg to the install target
# Other reasonable destinations:
# $(HOME)/.local/share/fonts
# $(HOME)/.fonts
# /usr/share/fonts/X11/misc
# See https://github.com/wch/extrafont/issues/52

SHELL=/bin/bash


all: 9x18.pcf.gz

9x18.pcf.gz:
	for i in *.bdf ; do \
	  bdftopcf $$i >$${i%.bdf}.pcf ; \
	done
	gzip -9 *.pcf

install: 9x18.pcf.gz
	test -e $(whereto) && test -d $(whereto) || mkdir -p $(whereto)
	mv *.pcf.gz $(whereto)
	cd $(whereto) ; mkfontdir
	xset +fp $(whereto) # update the font-path for the current session

clean:
	rm -f fonts.dir *.pcf *.gz *~





