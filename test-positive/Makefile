.DEFAULT_GOAL := test

MMCLI_CONTAINER_BUILD := docker build -t mmcli ../ 
MMCLI_CONTAINER_RUN := docker run -it -v $(CURDIR):/data mmcli --width=1920 --height=1080
MERMAID_FILES := $(shell find *.mmd)

build:
	$(MMCLI_CONTAINER_BUILD)
.PHONY: build

test: build
	$(foreach target,$(MERMAID_FILES), \
		$(MMCLI_CONTAINER_RUN) -i /data/$(target) -o /data/$(target).png ; \
	)
.PHONY: test