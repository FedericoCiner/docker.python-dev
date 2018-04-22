SHELL=/bin/bash

tUSER=$(shell ./get_user.sh)
repo_tag=federicociner

build_dir=latest

image_name=python3-notebook
image_tag=${image_name}:$(build_dir)
full_image_tag=$(repo_tag)/$(image_tag)

user_id=$$(id -u)
group_id=$$(id -g)
container_name=python3-notebook

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

runlocal:
	@echo "Running container locally"
	sudo docker run --name $(container_name) -d -p $(PORTP):8888 -v ~/workspace:/home/notebook:z $(full_image_tag)

runbash:
	docker exec -it $(image_name) /bin/bash -c "export COLUMNS=`tput cols`; export LINES=`tput lines`; exec bash"

.PHONY: buildlocal build runlocal runbash
