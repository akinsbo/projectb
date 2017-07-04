#.SILENT
IMAGE_NAME = image-name
CONTAINER_NAME = container-name
TAG_NAME = 0.01
CONTAINER_PORT = 3000
HOST_PORT = 3002
REACT_DEV_DIR = /home/olaolu/Documents/projectb/dev/frontend_dev/

#using space or tab is an important choice in formatting @echo statements
help:
	@echo
	@echo "Author: Olaolu Akinsete"
	@echo
	@echo " Commands: "
	@echo "	help - show this message"
	@echo "	docker-build - build docker image if not already done"
	@echo "	docker-run -  start this service, and all of its deps, locally(docker)"
	@echo "	docker-stop - stop and remove container and image"
	@echo "	docker-url - view url"
	@echo "	test-producer	- Run the unit tests for the procuder"
	@echo "	deps - Check for all dependecies"

docker-build:
	@echo "	first install node modules for building reactjs if not installed - i.e. no node_modules folder present"
	sudo npm install
	@echo	"	running build of react-js in case build folder does not exist - i.e. no build folder present"
	sudo npm run build
	@echo "	building docker image"
	sudo docker build -t $(IMAGE_NAME):$(TAG_NUMBER) .

docker-run:
	@echo	"	updating build folder of react-js"
	sudo npm run build
	@echo "	running docker image with volume mount at "
	sudo docker run -d -p $(HOST_PORT):$(CONTAINER_PORT) /
	-v $(REACT_DEV_DIR)/build/:/var/www/html/ /
	--name $(CONTAINER_NAME) $(IMAGE_NAME)

docker-stop:
	sudo docker stop $(CONTAINER_NAME)
	sudo docker rm $(CONTAINER_NAME)
	sudo docker rmi $(IMAGE_NAME)

docker-url:
	curl http://localhost:$(HOST_PORT)

deps:
	@echo "	*docker"