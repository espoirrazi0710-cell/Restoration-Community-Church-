SHELL := /bin/bash
.PHONY: sass watch serve start

sass:
	sass assets/sass:assets/css --no-source-map --style=expanded

watch:
	sass --watch assets/sass:assets/css

serve:
	python3 -m http.server 8000

start:
	@$(MAKE) sass & $(MAKE) serve
