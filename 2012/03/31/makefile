.PHONY = all, clean, copy, gen

SRC   = src
BUILD = build
BUILD.STYLE.CSS = $(BUILD)/css/style.css
TOOLS = ~/tools

HTMLCOMPRESSOR = $(TOOLS)/htmlcompressor-1.5.2.jar
YUICOMPRESSOR  = $(TOOLS)/yuicompressor-2.4.7.jar
PREFIXR        = http://prefixr.com/api/index.php

all :  clean gen

clean:
	rm -rf $(BUILD)

copy:
	mkdir -p $(BUILD)/css
	cp $(SRC)/css/style.css $(BUILD)/css

gen: copy
	java -jar $(HTMLCOMPRESSOR) -o $(BUILD)/index.html --compress-js --compress-css $(SRC)/index.html
	@curl -sSd css="$(shell cat $(BUILD.STYLE.CSS))" $(PREFIXR) -o $(BUILD.STYLE.CSS)
	@echo Added Missing Vendor prefixes to stylesheets
	java -jar $(YUICOMPRESSOR) -o $(BUILD.STYLE.CSS) $(BUILD.STYLE.CSS)




