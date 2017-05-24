HTMLDIR=/home/zeus/httpd/html/texts
HTMLDIR_LAB=/home/zeus/httpd/html/lab/texts
LATEX2HTML=latex2html -split +1
#LATEX2HTML=hevea
HEVEA=hevea
CP=cp -dRuv
.SUFFIXES: .md .pdf .tex .dvi

clean:
	rm -f *.aux *.log *.bbl *.blg *.toc *.dvi *~ *.fdb_latexmk *.fls *.synctex.gz


### use latex2html for html conversion for the following documents
install-back-restore: back-restore
	${LATEX2HTML} $<
	chmod 664 back-restore.{pdf,ps,dvi,html}
	${CP} back-restore.pdf ${HTMLDIR_LAB}
	${CP} back-restore.ps ${HTMLDIR_LAB}
	${CP} back-restore.dvi ${HTMLDIR_LAB}
#	sed 's/ISO-8859-1/euc-jp/' $<.html > ${HTMLDIR}/$<.html
	chmod 775 $<
	chmod 664 $</*
	${CP} -dur $< ${HTMLDIR_LAB}

install-lam: lam
	${LATEX2HTML} $<
	chmod 664 lam.{pdf,ps,dvi}
	${CP} lam.pdf ${HTMLDIR_LAB}
	${CP} lam.ps ${HTMLDIR_LAB}
	${CP} lam.dvi ${HTMLDIR_LAB}
	${CP} info_mpi.tgz ${HTMLDIR_LAB}
#	sed 's/ISO-8859-1/euc-jp/' $<.html > ${HTMLDIR}/$<.html
	chmod 775 $<
	chmod 664 $</*
	${CP} -dur $< ${HTMLDIR_LAB}


lam: lam.dvi lam.ps lam.pdf
	${LATEX2HTML} $<

.SUFFIXES: .tex .ps .html .pdf

.tex.dvi:
	platex $<
	platex $<
	platex $<

.tex.html:
	${HEVEA} $<
	${HEVEA} $< # requires two run to check label info
#	${LATEX2HTML} $<

.dvi.ps:
	dvips $<

.dvi.pdf:
	dvipdfmx $<


.md.pdf:
	md2ptex $<
	platex $*-md.tex
	platex $*-md.tex
	dvipdfmx $*-md.dvi
	mv $*-md.pdf $*.pdf

