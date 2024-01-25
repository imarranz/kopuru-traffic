#                    _           __  _  _
#                   | |         / _|(_)| |
#  _ __ ___    __ _ | | __ ___ | |_  _ | |  ___
# | '_ ` _ \  / _` || |/ // _ \|  _|| || | / _ \
# | | | | | || (_| ||   <|  __/| |  | || ||  __/
# |_| |_| |_| \__,_||_|\_\\___||_|  |_||_| \___|
#

# Uso de Variables en makes
# https://ftp.gnu.org/old-gnu/Manuals/make-3.79.1/html_chapter/make_6.html

TEMPLATE = "./templates/kopuru-template.tex"
TOP_LEVEL_DIVISION = "chapter"
TITLEPAGE_COLOR = "EEEEEE"
TITLEPAGE_RULE_HEIGHT = 8
TITLEPAGE_BACKGROUND = "./templates/figures/titlepage-background-template.pdf"
PAGE_BACKGROUND = "./templates/figures/page-background-template.pdf"
PAGE_BACKGROUND_OPACITY = 0.2
FOOTER_RIGHT = "Página \thepage"
INSTITUTE = "Ibon Martínez-Arranz"
AUTHOR = "Ibon Martínez-Arranz"
TITLEBOOK = "Predicción del tráfico a la entrada de un Polígono Industrial Vasco"
INTERMEDIATE_OUTPUT = "book"
INFO = "pdf.info"

createpy:
	jupyter nbconvert --to python 20231130-IMA-Exploratory_Data_Analysis.ipynb
	jupyter nbconvert --to python 20231201-IMA-Modelling.ipynb

createmarkdownbook:

	jupyter nbconvert --to markdown\
		--no-prompt\
		--TagRemovePreprocessor.remove_input_tags remove_input_markdown\
		--TagRemovePreprocessor.remove_cell_tags remove_cell_markdown\
		--TagRemovePreprocessor.remove_all_outputs_tags remove_output_markdown\
		20240101-IMA-Introduction.ipynb

	jupyter nbconvert --to markdown\
		--no-prompt\
		--TagRemovePreprocessor.remove_input_tags remove_input_markdown\
		--TagRemovePreprocessor.remove_cell_tags remove_cell_markdown\
		--TagRemovePreprocessor.remove_all_outputs_tags remove_output_markdown\
		20231130-IMA-Exploratory_Data_Analysis.ipynb
	jupyter nbconvert --to markdown\
		--no-prompt\
		--TagRemovePreprocessor.remove_input_tags remove_input_markdown\
		--TagRemovePreprocessor.remove_cell_tags remove_cell_markdown\
		--TagRemovePreprocessor.remove_all_outputs_tags remove_output_markdown\
		20231201-IMA-Modelling.ipynb

	mv 20240101-IMA-Introduction.md ./book/20240101-IMA-Introduction.md

	mv 20231130-IMA-Exploratory_Data_Analysis.md ./book/20231130-IMA-Exploratory_Data_Analysis.md
	#mv ./20231130-IMA-Exploratory_Data_Analysis_files ./book/

	mv 20231201-IMA-Modelling.md ./book/20231201-IMA-Modelling.md
	#mv ./20231201-IMA-Modelling_files ./book/

createsimplepdfbook:
	pandoc book/000_title.md \
		book/20240101-IMA-Introduction.md \
		book/20231130-IMA-Exploratory_Data_Analysis.md \
		book/20231201-IMA-Modelling.md \
		--output $(INTERMEDIATE_OUTPUT)".pdf" \
		--from markdown \
		--template $(TEMPLATE) \
		--toc \
		--variable book=True \
		--top-level-division $(TOP_LEVEL_DIVISION) \
		--listings \
		--variable titlepage=True \
		--variable titlepage-color=$(TITLEPAGE_COLOR) \
		--variable titlepage-rule-height=$(TITLEPAGE_RULE_HEIGHT) \
		--variable titlepage-background=$(TITLEPAGE_BACKGROUND) \
		--variable footer-right=$(FOOTER_RIGHT) \
		--variable linkcolor=primaryowlorange \
		--variable urlcolor=primaryowlorange \
		--variable institute=$(INSTITUTE) \
		--filter pandoc-latex-environment \
		--metadata=title:$(TITLEBOOK) \
		--metadata=author:$(AUTHOR)

	pdftk "book.pdf" update_info_utf8 $(INFO) output "book2.pdf"

	# https://www.adobe.com/acrobat/hub/how-to-compress-pdf-in-linux.html
	# Con este comando reducimos el tamaño del documento final
	gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen -dNOPAUSE -dQUIET -dBATCH -sOutputFile=$(TITLEBOOK)".pdf" "book2.pdf"

	# Eliminamos un fichero auxiliar
	rm "book.pdf" "book2.pdf"

makezip:
	zip TraficoDataEvaluado_IBON_v01.zip \
		$(TITLEBOOK)".pdf" \
		20231130-IMA-Exploratory_Data_Analysis.py \
		20231201-IMA-Modelling.py \
		TraficoDataEvaluado_IBON_v01.csv


createpdfbook:
	pandoc book/000_title.md \
		book/20240101-IMA-Introduction.md \
		book/20231130-IMA-Exploratory_Data_Analysis.md \
		book/20231201-IMA-Modelling.md \
		--output $(INTERMEDIATE_OUTPUT)".pdf" \
		--from markdown \
		--template $(TEMPLATE) \
		--toc \
		--variable book=True \
		--top-level-division $(TOP_LEVEL_DIVISION) \
		--listings \
		--variable titlepage=True \
		--variable titlepage-color=$(TITLEPAGE_COLOR) \
		--variable titlepage-rule-height=$(TITLEPAGE_RULE_HEIGHT) \
		--variable titlepage-background=$(TITLEPAGE_BACKGROUND) \
		--variable page-background=$(PAGE_BACKGROUND) \
		--variable page-background-opacity=$(PAGE_BACKGROUND_OPACITY) \
		--variable footer-right=$(FOOTER_RIGHT) \
		--variable linkcolor=primaryowlorange \
		--variable urlcolor=primaryowlorange \
		--variable institute=$(INSTITUTE) \
		--filter pandoc-latex-environment \
		--metadata=title:$(TITLEBOOK) \
		--metadata=author:$(AUTHOR)

	# Con pdftk aǹadimos la cubierta y la página de los autores
	pdftk templates/figures/cover.pdf \
	      templates/figures/page-white-template.pdf \
	      templates/figures/page-authors-template.pdf \
	      templates/figures/page-white-template.pdf \
	      $(INTERMEDIATE_OUTPUT)".pdf" cat output $(INTERMEDIATE_OUTPUT)"2.pdf"

	# Con pdftk aǹadimos información al documento en pdf
	pdftk $(INTERMEDIATE_OUTPUT)"2.pdf" update_info_utf8 $(INFO) output $(TITLEBOOK)".pdf"

	# Eliminamos los documentos auxiliares que hemos generado para construir el documento final
	rm $(INTERMEDIATE_OUTPUT)".pdf" $(INTERMEDIATE_OUTPUT)"2.pdf"

	# https://www.adobe.com/acrobat/hub/how-to-compress-pdf-in-linux.html
	# Con este comando reducimos el tamaño del documento final
	gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen -dNOPAUSE -dQUIET -dBATCH -sOutputFile=$(TITLEBOOK)"2.pdf" $(TITLEBOOK)".pdf"

	# Eliminamos un fichero auxiliar
	rm $(TITLEBOOK)".pdf"

	# Renombramos el documento final
	mv $(TITLEBOOK)"2.pdf" $(TITLEBOOK)".pdf"


#pdftk "Predicción del tráfico a la entrada de un Polígono Industrial Vasco.pdf" update_info_utf8 "pdf.info" output "prueba.pdf"
