DOCKER_IMAGE_NAME := {{ cookiecutter.docker_image_name }}
VOLUME_FILE := ~/.docker-volumes.txt


.PHONY: image
image:
	docker build -t $(DOCKER_IMAGE_NAME) .

.PHONY: run
run:
	@VOLUME_ARGS=""
	@while IFS= read -r line; do \
		VOLUME_ARGS="$$VOLUME_ARGS -v $$line"; \
	done < $(VOLUME_FILE); \
	docker run $$VOLUME_ARGS \
		--gpus all \
		--rm \
		--ipc=host --ulimit memlock=-1 --ulimit stack=67108864 \
		--memory-swap=-1 \
		--network=host \
		--name $(DOCKER_IMAGE_NAME)_$(USER) \
		-it $(DOCKER_IMAGE_NAME) \
		/bin/bash -l
