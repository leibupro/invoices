# invoices
## Overview
Very simple and pragmatic invoice document processor.

For extensive information consult the verbose header comments of the Makefile (`./INVOICES/Makefile`), the preamble file (`./INVOICES/template/factura_preamble.tex`) and the template file (`./INVOICES/template/factura_template.tex`). For personal use, the preamble and template file have to be adjusted accordingly.

The tree appears as follows:

```
                  Files created by the Makefile
                  are highlighted with [] braces:
                  
                  ./INVOICES
                    |-- Makefile
                    |-- template
                    |   |-- factura_preamble.tex
                    |   +-- factura_template.tex
                    |-- customer_1
                    |   |-- customer.txt
                    |   |-- invoice_1
                    |   |   |-- invoice_1.tex
                    |   |   +-- [invoice_1.pdf]
                    |   |-- invoice_2
                    |   |   |-- invoice_2.tex
                    |   |   +-- [invoice_2.pdf]
                    |   +-- invoice_n
                    |       |-- invoice_n.tex
                    |       +-- [invoice_n.pdf]
                    +-- customer_2 
                        |-- customer.txt
                        +-- invoice_1
                            |-- invoice_1.tex
                            +-- [invoice_1.pdf]

```

## Prerequisites
* GNU Make
* TEX processor. In this make recipe pdflatex is used.
* To develop this project the texlive-full package was used. Maybe a smaller texlive package is sufficient.
 
## Remarks 
* Be careful by using the clean target. It removes all the invoice PDF files. If all the invoices are rebuilt afterwards, the date of today will appear on all the rebuilt invoices.

## License
```
"THE BEER-WARE LICENSE" (Revision 42):
<pl@vqe.ch> wrote these files.    As long as you retain this notice you
can do whatever you want with this stuff. If we meet some day, and you think
this stuff is worth it, you can buy me a beer in return.   P. Leibundgut
```
