---
---
PATH  := ../node_modules/.bin:$(PATH)

FA_ROOT_DIRECTORY = assets/fork-awesome
FA_LESS_DIRECTORY = assets/fork-awesome/less
FA_SCSS_DIRECTORY = assets/fork-awesome/scss
FA_CSS_DIRECTORY = assets/fork-awesome/css

FA_LESS_MODERN = ${FA_LESS_DIRECTORY}/fork-awesome.less
FA_SCSS_MODERN = ${FA_SCSS_DIRECTORY}/fork-awesome.scss

FA_CSS_MODERN = ${FA_CSS_DIRECTORY}/fork-awesome.css
FA_CSS_MODERN_MIN = ${FA_CSS_DIRECTORY}/fork-awesome.min.css

SITE_LESS_DIRECTORY = assets/less
SITE_CSS_DIRECTORY = assets/css

SITE_LESS = ${SITE_LESS_DIRECTORY}/site.less
SITE_CSS = ${SITE_CSS_DIRECTORY}/site.css

build:
	@echo "Compiling Less files"
	@mkdir -p ${FA_CSS_DIRECTORY}

	lessc ${FA_LESS_MODERN} ${FA_CSS_MODERN}
	lessc --clean-css="--compatibility=ie8" --source-map ${FA_CSS_MODERN} ${FA_CSS_MODERN_MIN}

	lessc --clean-css="--compatibility=ie8" --source-map ${SITE_LESS} ${SITE_CSS}

	@echo "Moving CSS, LESS & SASS to /"
	cp -r ${FA_ROOT_DIRECTORY}/ ../
	mv ../scss/fork-awesome.scss.txt ../scss/fork-awesome.scss

	@echo "Moving font files to assets"
	cp -r ../fonts ${FA_ROOT_DIRECTORY}/

	@echo "Updating Readme"
	mv README.md-nobuild ../README.md

default: build


.PHONY: build
