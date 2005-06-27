.PHONY: all upload

all: vpp43.html index.html pyvisa.pdf pyvisa

vpp43.html: vpp43.txt
	rst2html.py vpp43.txt > vpp43.html

index.html: homepage.txt
	rst2html.py homepage.txt > index.html

# I have to do the following in /tmp because latex2html doesn't want to work in
# a path that contains a dot.  Unfortunately, the BUILD directory that
# Distutils creates contains one.

pyvisa.pdf: pyvisa.tex
	rm -Rf pyvisa /tmp/pyvisa
	cp pyvisa.tex /tmp/
	cd /tmp ; mkhowto --pdf --html \
	  --up-link http://pyvisa.sourceforge.net \
	  --up-title "PyVISA homepage" pyvisa.tex
	mv /tmp/pyvisa.pdf /tmp/pyvisa .

upload: all
	scp vpp43.html index.html default.css pyvisa.pdf \
	  shell.sf.net:/home/groups/p/py/pyvisa/htdocs/
	scp -r pyvisa/* shell.sf.net:/home/groups/p/py/pyvisa/htdocs/pyvisa/