build:
	bundle exec jekyll b

commit: build
	git add .
	git commit -m 'release'

push: commit
	git push origin master

deploy: push
	bundle exec cap production deploy
