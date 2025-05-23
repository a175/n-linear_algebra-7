PDFLATEX=dvipdfmx
LATEX=platex
#BIBTEX=bibtex
BIBTEX=pbibtex
DVI2PDF=dvipdfmx
TEXFILE=x2
MAINTEXFILES=p.tex numberedproof.sty
MENDEX=mendex
DICFILE=terms.dic
INDEXSTY=jpbase.ist

all: pdf
dvi: ${TEXFILE}.dvi
pdf: ${TEXFILE}.pdf

${TEXFILE}.dvi: ${TEXFILE}.tex ${MAINTEXFILES} ${TEXFILE}.bbl ${TEXFILE}.ind
	${LATEX} ${TEXFILE} && ${LATEX} ${TEXFILE}

${TEXFILE}.pdf: ${TEXFILE}.dvi
	${DVI2PDF} ${TEXFILE}.dvi
#${TEXFILE}.pdf: ${TEXFILE}.tex ${MAINTEXFILES} ${TEXFILE}.bbl
#	${PDFLATEX} ${TEXFILE} && ${PDFLATEX} ${TEXFILE}

bbl:${TEXFILE}.bbl
${TEXFILE}.bbl:
	${LATEX} ${TEXFILE} && ${BIBTEX} ${TEXFILE}

ind: ${TEXFILE}.ind
${TEXFILE}.ind: ${DICFILE}
	${LATEX} ${TEXFILE} && ${MENDEX} -r -c -g -s ${INDEXSTY} -U -d ${DICFILE} -p any ${TEXFILE}


view:
	evince ${TEXFILE}.pdf &
clean:
	rm -f ${TEXFILE}.dvi ${TEXFILE}.pdf ${TEXFILE}.log ${TEXFILE}.toc ${TEXFILE}.aux ${TEXFILE}.bbl ${TEXFILE}.blg  ${TEXFILE}.ilg ${TEXFILE}.ind  ${TEXFILE}.idx  ${TEXFILE}.out texput.log
