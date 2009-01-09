require 'rubygems'
require 'rake'
require 'rake/testtask'
require 'rake/rdoctask'
require 'rake/gempackagetask'
require 'date'

desc 'Default: run unit tests.'
task :default => :test

desc 'Test the inaction_mailer plugin.'
Rake::TestTask.new(:test) do |t|
  t.libs << 'lib'
  t.pattern = 'test/**/*_test.rb'
  t.verbose = true
end

spec = Gem::Specification.new do |s|
  s.name        = %q{inaction_mailer}
  s.version     = "0.5"
  s.summary     = %q{An ActionMailer delivery mechanism to save mails as files in a directory.}
  s.description = %q{An ActionMailer delivery mechanism to save mails as files in a directory.}

  s.files        = FileList['[A-Z]*', 'lib/**/*.rb', 'test/**/*.rb', 'rails/*']
  s.require_path = 'lib'
  s.test_files   = Dir[*['test/**/*_test.rb']]

  s.has_rdoc         = true
  s.extra_rdoc_files = ["README.markdown"]
  s.rdoc_options = ['--line-numbers', '--inline-source', "--main", "README.markdown"]

  s.authors = ["Tom Lea"]
  s.email   = %q{commits@tomlea.co.uk}

  s.platform = Gem::Platform::RUBY
end

Rake::GemPackageTask.new spec do |pkg|
  pkg.need_tar = true
  pkg.need_zip = true
end

desc "Clean files generated by rake tasks"
task :clobber => [:clobber_rdoc, :clobber_package]

desc "Generate a gemspec file"
task :gemspec do
  File.open("#{spec.name}.gemspec", 'w') do |f|
    f.write spec.to_ruby
  end
end
