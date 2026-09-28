source "https://rubygems.org"
# Hello! This is where you manage which Jekyll version is used to run.
# When you want to use a different version, change it below, save the
# file and run `bundle install`. Run Jekyll with `bundle exec`, like so:
#
#     bundle exec jekyll serve
#
# This will help ensure the proper Jekyll version is running.
# Happy Jekylling!
# The site is deployed by GitHub Pages' built-in build, so build locally with
# the same gem set. To upgrade, run `bundle update github-pages`.
gem "github-pages", group: :jekyll_plugins
# If you have any plugins, put them here!
# (Versions are pinned by github-pages.)
group :jekyll_plugins do
  gem "jekyll-feed"
  gem "jekyll-paginate"
end

# Ruby 3 no longer bundles webrick, which `jekyll serve` needs.
gem "webrick"

# Windows and JRuby does not include zoneinfo files, so bundle the tzinfo-data gem
# and associated library.
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo"
  gem "tzinfo-data"
end

# Performance-booster for watching directories on Windows
gem "wdm", "~> 0.1.1", :platforms => [:mingw, :x64_mingw, :mswin]

