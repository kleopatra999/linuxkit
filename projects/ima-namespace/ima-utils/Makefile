.PHONY: tag push
default: push

IMAGE=ima-utils
DEPS=Dockerfile

HASH?=$(shell git ls-tree HEAD -- ../$(notdir $(CURDIR)) | awk '{print $$3}')

tag: $(DEPS)
	docker build --no-cache -t linuxkit/$(IMAGE):$(HASH) .

push: tag
	docker pull linuxkit/$(IMAGE):$(HASH) || \
	docker push linuxkit/$(IMAGE):$(HASH)
