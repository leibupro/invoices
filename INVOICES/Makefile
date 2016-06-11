#  ############################################################
#
#
#   File:          Makefile
#
#
#   Purpose:       This file contains the necessary
#                  pixie dust to process all the
#                  invoice tex sources located
#                  in the customer directories.
#                  As output results a PDF file for
#                  each invoice, where there is no
#                  pre existent PDF file or the tex
#                  source was later modified than
#                  the pre existent PDF file.
#                  
#                  Tree example:
#                  Files created by this Makefile
#                  are highlighted with [] braces:
#                  
#                  ./INVOICES
#                    |-- Makefile (this file)
#                    |-- template
#                    |   |-- sender_information.tex
#                    |   |-- factura_preamble.tex
#                    |   +-- factura_template.tex
#                    |-- customer_1
#                    |   |-- customer.txt
#                    |   |-- invoice_1
#                    |   |   |-- invoice_1.tex
#                    |   |   +-- [invoice_1.pdf]
#                    |   |-- invoice_2
#                    |   |   |-- invoice_2.tex
#                    |   |   +-- [invoice_2.pdf]
#                    |   +-- invoice_n
#                    |       |-- invoice_n.tex
#                    |       +-- [invoice_n.pdf]
#                    +-- customer_2 
#                        |-- customer.txt
#                        +-- invoice_1
#                            |-- invoice_1.tex
#                            +-- [invoice_1.pdf]
#
#
#   Remarks:       - A TEX processor is required.
#                    In this make recipe pdflatex
#                    is used.
#
#                  - To develop this project
#                    the texlive-full package
#                    was used. Maybe a smaller
#                    texlive package is sufficient.
#                   
#                  - Be careful by using the clean
#                    target. It removes all the
#                    invoice PDF files.
#                    If all the invoices are
#                    rebuilt afterwards, the date 
#                    of today will appear on all 
#                    the rebuilt invoices.
# 
#
#   Author:        P. Leibundgut <leiu@zhaw.ch>
#                                <pl@vqe.ch>
#
#
#   Date:          06/2016
#
#
#  ############################################################

TEX = pdflatex

PREAMBLE = ./template/factura_preamble.tex
TEMPLATE = ./template/factura_template.tex
SENDER   = ./template/sender_information.tex

EXCLUDE_DIR = ./template


SRC   = $(shell find . -name "*.tex" -not -path "$(EXCLUDE_DIR)/*")

PDF   = $(SRC:.tex=.pdf)

CUST  = customer.txt


.PHONY: all clean


all: $(PDF)


%.pdf: %.tex $(PREAMBLE) $(TEMPLATE) $(SENDER)
	@if [ -f $(firstword $(subst /, ,$<))/$(CUST) ];\
  then\
    echo "$(CUST) file found.";\
    \
    TEXINPUTS=$(dir $(PREAMBLE)):$(firstword $(subst /, ,$<)): \
    $(TEX) -output-directory $(dir $@) $<;\
    TEXINPUTS=$(dir $(PREAMBLE)):$(firstword $(subst /, ,$<)): \
    $(TEX) -output-directory $(dir $@) $<;\
    \
    # $(subst from,to,text) \
    rm $(subst .pdf,.aux,$@);\
    rm $(subst .pdf,.log,$@);\
    rm $(subst .pdf,.out,$@);\
  else\
    echo "$(CUST) file not found.";\
  fi


clean:
	rm $(PDF)
