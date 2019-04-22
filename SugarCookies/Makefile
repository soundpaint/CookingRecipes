OBJ=receipt.pdf
IMAGES=header.png
BUILD_DIR=build
LATEX_OPTS=--output-directory=$(BUILD_DIR)

all: $(BUILD_DIR) $(OBJ)

objclean:
	rm -rf $(BUILD_DIR)

bkpclean:
	rm -f *~

clean: objclean

dstclean: objclean bkpclean

$(BUILD_DIR):
	mkdir -p $@

%.pdf: %.tex $(IMAGES)
	pdflatex $(LATEX_OPTS) -shell-escape "$<"

tarball: dstclean
	@TGZ_DATE=`date +%Y-%m-%d_%H-%M-%S` ; \
	PROJECT_NAME=SugarCookies ; \
	PROJECT_PATH=`basename \`pwd\`` ; \
	TGZ_PREFIX=$$PROJECT_NAME\_$$TGZ_DATE ; cd .. ; \
	tar cvf ./$$TGZ_PREFIX.tar.bz2 \
		--transform=s/$$PROJECT_PATH/$$TGZ_PREFIX/ \
		--bzip2 $$PROJECT_PATH
