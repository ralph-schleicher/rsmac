## GNUmakefile --- make file for Ralph's TeX and LaTeX macros

# Copyright (C) 2023 Ralph Schleicher

# Redistribution and use in source and binary forms, with or without
# modification, are permitted provided that the following conditions
# are met:
#
#    * Redistributions of source code must retain the above copyright
#      notice, this list of conditions and the following disclaimer.
#
#    * Redistributions in binary form must reproduce the above copyright
#      notice, this list of conditions and the following disclaimer in
#      the documentation and/or other materials provided with the
#      distribution.
#
#    * Neither the name of the copyright holder nor the names of its
#      contributors may be used to endorse or promote products derived
#      from this software without specific prior written permission.
#
# THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
# "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
# LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS
# FOR A PARTICULAR PURPOSE ARE DISCLAIMED.  IN NO EVENT SHALL THE
# COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT,
# INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING,
# BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES;
# LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER
# CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT
# LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN
# ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE
# POSSIBILITY OF SUCH DAMAGE.

## Code:

texmfdir = $(HOME)/lib/texmf

LATEX = pdflatex
LATEX_FLAGS = -interaction=nonstopmode -file-line-error -shell-escape

rsmacdir = $(texmfdir)/tex/latex/rsmac
rsmac_DATA = rsmac.sty rsdisplay.sty rsmetasyntax.sty rsdefinition.sty rsdatetime.sty

%.pdf: %.tex $(rsmac_DATA)
	-$(LATEX) $(LATEX_FLAGS) $<

.PHONY: all
all: $(rsmac_DATA)

.PHONY: install
install: install-data

.PHONY: install-data
install-data: all
	mkdir -p $(rsmacdir)
	for f in $(rsmac_DATA) ; do \
	  echo "install -c -m 644 $$f $(rsmacdir)" ; \
	  install -c -m 644 $$f $(rsmacdir) ; \
	done
	texhash $(texmfdir)

.PHONY: check
check: t-rsdisplay.pdf t-rsmetasyntax.pdf t-rsdefinition.pdf t-rsdatetime.pdf

.PHONY: clean
clean:
	rm -f *.aux *.dvi *.idx *.ind *.lof *.lot *.out *.toc

.PHONY: distclean
distclean: clean
	rm -f *.log *.pdf *.synctex.gz

## GNUmakefile ends here
