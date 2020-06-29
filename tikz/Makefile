FIGURES_TEX := $(wildcard src/*.tex)
FIGURES_PDF := $(FIGURES_TEX:src/%.tex=build/%.pdf)
FIGURES_LOG := $(FIGURES_TEX:src/%.tex=build/%.log)
FIGURES_AUX := $(FIGURES_TEX:src/%.tex=build/%.aux)
FIGURES_PNG := $(FIGURES_TEX:src/%.tex=build/%.png)

DOCKER_CMD := docker run  --rm -i --volume "`pwd`:/data" --user `id -u`:`id -g` --net=none blang/latex:ubuntu
PDFLATEX := $(DOCKER_CMD) pdflatex

all: $(FIGURES_PDF) $(FIGURES_PNG)

build/%.pdf: src/%.tex
	$(PDFLATEX) -output-directory build $<

build/%.png: build/%.pdf
	pdftoppm -png $< > $@ -r 300

clean:
	rm $(FIGURES_AUX) $(FIGURES_LOG) 

clean-output:
	rm $(FIGURES_PDF)

clean-all: clean clean-output