LATEX2HTML=latex2html -split +1
#LATEX2HTML=hevea
HEVEA=hevea
CP=cp -dRuv
.SUFFIXES: .md .pdf .tex .dvi

clean:
	rm -f *.aux *.log *.bbl *.blg *.toc *.dvi *~ *.fdb_latexmk *.fls *.synctex.gz

.SUFFIXES: .tex .ps .html .pdf

.tex.dvi:
	platex $<
	platex $<
	platex $<

.tex.html:
	${HEVEA} $<
	${HEVEA} $< # requires two run to check label info
#	${LATEX2HTML} $<

.dvi.pdf:
	dvipdfmx $<


.md.pdf:
	md2ptex $<
	platex $*-md.tex
	platex $*-md.tex
	dvipdfmx $*-md.dvi
	mv $*-md.pdf $*.pdf

