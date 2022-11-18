SOURCE=chapters
BUILD=build
BOOK={{cookiecutter.output_filename}}
pdf:
	pandoc \
		--filter pandoc-crossref \
		--pdf-engine=xelatex \
		--template=./templates/eisvogel-2.0.0.tex \
		--highlight-style tango \
		--toc \
		--number-sections \
		-o $(BUILD)/$(BOOK).pdf \
		-V CJKmainfont="Noto Serif CJK SC" \
		-V book \
		--top-level-division=chapter \
		--resource-path=./chapters/01:./chapters/02 \
		$(SOURCE)/meta.md $(SOURCE)/01/*.md $(SOURCE)/02/*.md

epub:
	docker run -it -v $(PWD):/work -w /work binblee/pandoc:2.13 \
		--filter pandoc-crossref \
		--css ./templates/epub.css \
		--toc \
		--number-sections \
		-o $(BUILD)/$(BOOK).epub \
		$(SOURCE)/meta.md $(SOURCE)/01/*.md $(SOURCE)/02/*.md

all: pdf epub

clean:
	rm $(BUILD)/book.*
