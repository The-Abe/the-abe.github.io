task :dev do
  sh "JEKYLL_ENV=development bundle exec jekyll serve --livereload --host 0.0.0.0 --port 4000"
end

task :clean do
  sh "bundle exec jekyll clean"
end

task :test do
  sh "bundle exec jekyll doctor"
end

task :build do
  sh "JEKYLL_ENV=production bundle exec jekyll build"
end

task :listtheme do
  sh "tree $(bundle info --path minima)"
end
