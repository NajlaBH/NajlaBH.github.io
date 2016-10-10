#Jeklly site step by step. October, 16 - BHNajla-Air.
## I. Requirements
#### I.1 Sandbox:
##### * Source 
[https://github.com/calabash](https://github.com/calabash/install)
##### * Install 
```curl -sSL https://raw.githubusercontent.com/calabash/install/master/install-osx.sh | bash```
##### * Run 
- Try1 : ```calabash-ios gen```
- Try2 : ```calabash-sandbox```
- Try3 : ```./calabash-sandbox```

##### * Update
```calabash-sandbox update```
##### * Remove 
```rm -r ${HOME}/.calabash/sandbox
$ curl -sSL https://raw.githubusercontent.com/calabash/install/master/install-osx.sh | bash```

#### I.2 Check Ruby status:
##### * Ruby version
```gem -v```
##### * Install dependencies
```gem install bundler```
##### * Install Nodes.js
```gem install node```

#### I.3 Jeklly:
##### * Source 
[https://jekyllrb.com/docs/usage/](https://jekyllrb.com/docs/usage/)

##### * Install 
```gem install jekyll```
##### * Check version
```jekyll -v```
##### * Build 
- Try1 : ```jekyll build --watch```
- Try2 : ```jekyll build```

##### * Run server 
```jekyll server```

- Adresse :[http://localhost:4000/](http://127.0.0.1:4000) 

##### * Docs
```jekyll-docs```
##### * Update 
```
gem update jekyll
gem update bundler
```

## II. Create new projects
### II.1 Create a blog project
##### * Build[ok]
```
jekyll new blog
cd blog
jekyll build
jekyll server
```
!!! Important !!!
- With sandbox, you have to be inside the project dir when you build otherwise you will find this error :

>*Liquid Exception: Could not locate the included file 'icon-github.html' in any of ["/UserName.github.io/_includes"]. Ensure it exists in one of those directories and, if it is a symlink, does not point outside your site source. in blog/about.md
jekyll 3.3.0 | Error:  Could not locate the included file 'icon-github.html' in any of ["/UserName.github.io/_includes"]. Ensure it exists in one of those directories and, if it is a symlink, does not point outside your site source.*

##### * Test[ok]
- Edit "_Config.yml" file to change your own parameters.

### II.1 Create from a template
##### * Build from template [https://github.com/daattali/beautiful-jekyll](https://github.com/daattali/beautiful-jekyll)
- Fork and rename the repository.
##### * Test [jekyll 3.3.0]
- Edit "_Config.yml" file.
##### * Debug Gemfile matter
First try - install dependencies:[no]

```
gem install execjs
gem install therubyracer
gem install github-pages
gem install jekyll-paginate
```
Second try - reinstall preview version:[no]

```
gem install jekyll -v 3.1.6`
gem install bundler -v 1.12.5
```
Third try - use bundle exec !! YOUPI !! :[ok]

```
calabash-sandbox
jekyll serve
```
>>Error: path/.calabash/sandbox/Gems/gems/bundler-1.13.2/lib/bundler/definition.rb:179:in `rescue in specs': Your bundle is locked to i18n (0.7.0), but that version could not be found in any of the sources listed in your Gemfile. If you haven't changed sources, that means the author of i18n (0.7.0) has removed it. You'll need to update your bundle to a different version of i18n (0.7.0) that hasn't been removed in order to install. (Bundler::GemNotFound)

- Solution : 
```bundle exec calabash-ios version```
>>Error:Your bundle is locked to i18n (0.7.0), but that version could not be found in any of the sources listed in your Gemfile. If you haven't changed sources, that means the author of i18n (0.7.0) has removed it. You'll need to update your bundle to a different version of i18n (0.7.0) that hasn't been removed in order to install.

- Solution : 
```
bundle install
bundle exec calabash-ios version
```
>>Error:bundler: failed to load command: calabash-ios (/Users/remindNahool/.calabash/sandbox/Gems/bin/calabash-ios)
Gem::LoadError: calabash-cucumber is not part of the bundle. Add it to Gemfile.

- Solution:Edit Gemfile. 
*Add:
```gem 'calabash-cucumber'```
*Run:
```bundle exec jekyll serve``` :)







