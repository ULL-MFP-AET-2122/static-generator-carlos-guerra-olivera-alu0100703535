task :default => :deploy do
  sh "git add .; git commit -am new-version; git push -u origin master"
  end
  
  task :serve do
  sh "bundle exec jekyll serve"
  end
  
  task :build do
  sh "bundle exec jekyll build"
  end
  
  task :bw do
  sh "bundle exec jekyll build --watch"
  end
  
  task :deploy do
  sh "cd _site; git init; git remote add origin https://github.com/CGuerra2021/cguerra2021.github.io; touch .nojekyll; git add .; git commit -am new-deploy; git push -u --force origin master"
  end