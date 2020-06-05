source "http://rubygems.org"

gemspec

git "https://github.com/refinery/refinerycms", branch: "master" do
  gem "refinerycms"

  group :test do
    gem "refinerycms-testing"
  end
end

# Database Configuration
unless ENV["TRAVIS"]
  gem "activerecord-jdbcsqlite3-adapter", platform: :jruby
  gem "sqlite3", platform: :ruby
end
if !ENV["TRAVIS"] || ENV["DB"] == "mysql"
  gem "activerecord-jdbcmysql-adapter", platform: :jruby
  gem "jdbc-mysql", "= 5.1.13", platform: :jruby
  gem "mysql2", platform: :ruby
end

if !ENV["TRAVIS"] || ENV["DB"] == "postgresql"
  gem "activerecord-jdbcpostgresql-adapter", platform: :jruby
  gem "pg", platform: :ruby
end

gem "jruby-openssl", platform: :jruby

# Refinery/rails should pull in the proper versions of these
gem "sass-rails"
# until the deprecated code in the template handler is removed
gem "coffee-rails" #, git:'https://github.com/rails/coffee-rails'
gem "uglifier"


group :development do
  gem 'listen'
end

group :test do
  gem "launchy"
end

# Load local gems according to Refinery developer preference.
if File.exist? local_gemfile = File.expand_path("../.gemfile", __FILE__)
  eval File.read(local_gemfile)
end
