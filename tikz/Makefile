FIGURES_TEX := $(wildcard src/*.tex)
FIGURES_PDF := $(FIGURES_TEX:src/%.tex=build/%.pdf)
FIGURES_LOG := $(FIGURES_TEX:src/%.tex=build/%.log)
FIGURES_AUX := $(FIGURES_TEX:src/%.tex=build/%.aux)

DOCKER_CMD := docker run  --rm -i --volume "`pwd`:/data" --user `id -u`:`id -g` --net=none blang/latex:ubuntu
PDFLATEX := $(DOCKER_CMD) pdflatex

all: $(FIGURES_PDF)

build/%.pdf: src/%.tex
	$(PDFLATEX) -output-directory build $<

clean:
	rm $(FIGURES_AUX) $(FIGURES_LOG) 

clean-output:
	rm $(FIGURES_PDF)

clean-all: clean clean-output