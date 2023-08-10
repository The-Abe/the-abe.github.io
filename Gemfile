source "https://rubygems.org"

gem "github-pages", group: :jekyll_plugins
group :jekyll_plugins do
  gem "jekyll-feed", "~> 0.12"
end

# Windows and JRuby does not include zoneinfo files, so bundle the tzinfo-data
# gem and associated library.
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end

# Performance-booster for watching directories on Windows
gem "wdm", "~> 0.1.1", :platforms => [:mingw, :x64_mingw, :mswin]

# Rake is a Make-like program implemented in Ruby.
gem "rake", "~> 13.0", :group => :development

# Server required for jekyll on Ruby > 3
gem "webrick", "~> 1.8", :group => :development

# Catches exceptions and retries each request a limited number of times
# As requested by jekyll serve.
gem "faraday-retry", "~> 2.2", :group => :development

gem "jekyll-paginate", "~> 1.1"
