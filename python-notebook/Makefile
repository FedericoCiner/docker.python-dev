SHELL=/bin/bash

tUSER=$(shell ./get_user.sh)
repo_tag=federicociner

build_dir=latest

image_tag=python-notebook:$(build_dir)

full_image_tag=$(repo_tag)/$(image_tag)

user_image_tag=usernotebook:$(tUSER)

user_id=$$(id -u)
group_id=$$(id -g)

ifeq ($(PORTP),)
PORTP=8888
endif

testuser:
	@echo $$USER
	@echo $(tUSER)
	@echo $(user_id)
	@echo $(group_id)
buildlocal:
	@echo "Building container"
	sudo docker build $(build_dir) --tag $(full_image_tag)

build:
	@echo "Building container"
	sudo docker build $(build_dir)

runlocal-jupyter: buildlocal
	@echo "Running container locally"
	sudo docker run -d -p $(PORTP):8888 -v ~/Projects:/home/notebook:z $(full_image_tag) jupyter notebook

runlocal-bash: buildlocal
	@echo "Running container locally"
	sudo docker run -it -p $(PORTP):8888 -v ~/Projects:/home/notebook:z $(full_image_tag) bash

containername:
	@echo $(user_image_tag)

.PHONY: buildlocal build runlocal