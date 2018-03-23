compile:
	@mkdir -p output/
	@echo "compiled file" > output/binary

test:
	@echo "---\nHello 👋 \n---\nI am running my tests..."
	@sleep 3
	@ls -la output/
	@echo "...Done!"

style-checking:
	@echo "---\nChecking your changes for style errors..."
	@sleep 3
	@echo "...Done!"


scan-flaws:
	@echo "---\nScanning..."
	@sleep 2
	@echo "...Done!"

client-performance:
	@echo "---\nPerformance testing of the application..."
	@sleep 2
	@echo "...targeting '$target' for testing..."
	@echo "...Done!"

deploy:
	@echo "---\nDeploying to '$env' environment..."
	@sleep 1
	@echo "...Done!"



help:
	@grep -E '^[a-zA-Z_-]+:.*?## .*$$' $(MAKEFILE_LIST) | awk 'BEGIN {FS = ":.*?## "}; {printf "\033[36m%-20s\033[0m %s\n", $$1, $$2}'

.PHONY: compile test style-checking scan-flaws deploy slack-deploy-ready
