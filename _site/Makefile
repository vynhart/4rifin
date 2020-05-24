build:
	bundle exec jekyll b

commit: build
	git add .
	git commit -m 'release'

push:
	git push origin master

deploy:
	bundle exec cap production deploy
