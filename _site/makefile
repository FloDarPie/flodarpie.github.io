# Variables
JEKYLL = bundle exec jekyll
BUILD_DIR = _site
DEV_BRANCH = dev
PROD_BRANCH = main
MESSAGE ?= "Mise à jour du site"

# Règles principales
.PHONY: serve build clean publish update

## Lancer le serveur local avec surveillance
serve:
	$(JEKYLL) serve --livereload

## Générer le site statique dans _site/
build:
	$(JEKYLL) build

## Nettoyer les fichiers générés
clean:
	rm -rf $(BUILD_DIR)

## Mettre à jour la branche de développement et pousser
update:
	git add .
	git commit -m "$(MESSAGE)" || true
	git push origin $(DEV_BRANCH)

## Publier sur la branche production
publish:
	git checkout $(PROD_BRANCH)
	git merge $(DEV_BRANCH)
	$(JEKYLL) build
	git add $(BUILD_DIR)
	git commit -m "Publication: $(MESSAGE)" || true
	git push origin $(PROD_BRANCH)
	git checkout $(DEV_BRANCH)
