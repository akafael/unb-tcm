##
# Makefile for Latex + Pythontex
# @author Rafael Lima
##

# Compiler Options
TEX = pdflatex
TEXFLAGS = --enable-write18 --shell-escape
TEXAUXFILES = relat_capa.tex relat_layout.tex

NAME = lista1

##
# Recipes:
##
.PHONY = ALL
ALL: $(NAME).pdf

# Compile and open pdf
$(NAME).pdf: $(NAME).tex $(TEXAUXFILES) $(NAME).pytxcode
	$(TEX) $(TEXFLAGS) $(NAME).tex &&\
	$(TEX) $(NAME).tex &&\
	$(TEX) $(NAME).tex &&\
	xdg-open $(@)&

$(NAME).pytxcode: $(NAME).tex
	$(TEX) $(TEXFLAGS) $<
	pythontex $<

# Generate Python free latex code
.PHONY = pythonfree
pythonfree: $(NAME).tex
	depythontex $<

# Remove generated files
.PHONY = clean
clean-tex:
	rm -f $(NAME).aux $(NAME).bbl $(NAME).blg $(NAME).log $(NAME).idx $(NAME).out\
	$(NAME).nav $(NAME).snm $(NAME).toc $(NAME).vrb $(NAME).out

clean-py:
	rm -f $(NAME).py*
	rm -fr pythontex-files-*

.PHONY = clean-all
clean-all: clean-tex clean-py
	rm -f $(NAME).pdf
