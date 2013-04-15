TEXINPUTS=.:Styles//::
BSTINPUTS=.:Styles//::

TARGET=main
STY = ndisplay.sty liquidHaskell.sty ngrammar.sty
TEX = theorems.tex grammar.tex typing.tex operational.tex definitions.tex prfLmTransD.tex prfLmTransP.tex proofType.tex
BIB = myrefs
SRCFILES = Makefile  ${TEX} ${STY} ${BIB}.bib  




# make pdf by default
# all: ${TARGET}.pdf

all:
	pdflatex main
	bibtex main
	pdflatex main
	bibtex main
	pdflatex main

count:
	pdftotext main.pdf -| tr -d '.' | wc -w

clean:
	$(RM) *.log *.aux *.ps *.dvi *.bbl *.blg *.bak *.fdb_latexmk *~

reallyclean: clean
	$(RM) *.ps *.pdf

distclean: reallyclean

pdfshow: $(TARGET).pdf
	xpdf $(TARGET).pdf

acroshow: $(TARGET).pdf
	acroread $(TARGET).pdf

pack: reallyclean
	tar cvfz liquidHaskell_tex.tar.gz ${SRCFILES}

PHONY : ps all clean reallyclean distclean
