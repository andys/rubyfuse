require 'rubygems'
require 'rake'

begin
  require 'jeweler'
  Jeweler::Tasks.new do |gem|
    gem.name        = "rubyfuse"
    gem.summary     = "Define filesystems entirely in Ruby."
    gem.description = "RubyFuse lets programmers create a mounted filesystems entirely defined in Ruby."
    gem.email       = "jon@jonsview.com"
    gem.homepage    = "http://jonsview.com/projects/rubyfuse"
    gem.authors     = ["Jon Stacey", "Greg Millam"]

    # gem is a Gem::Specification... see http://www.rubygems.org/read/chapter/20 for additional settings
  end
rescue LoadError
  puts "Jeweler not available. Install it with: sudo gem install technicalpickles-jeweler -s http://gems.github.com"
end

# require 'rake/testtask'
# Rake::TestTask.new(:test) do |test|
#   test.libs << 'lib' << 'test'
#   test.pattern = 'test/**/*_test.rb'
#   test.verbose = true
# end
# 
# begin
#   require 'rcov/rcovtask'
#   Rcov::RcovTask.new do |test|
#     test.libs << 'test'
#     test.pattern = 'test/**/*_test.rb'
#     test.verbose = true
#   end
# rescue LoadError
#   task :rcov do
#     abort "RCov is not available. In order to run rcov, you must: sudo gem install spicycode-rcov"
#   end
# end


# task :default => :test

# task :export do
#   dirname = "fusefs-#{FuseFS::VERSION}"
#   sh %{cvs export -D now -d #{dirname} PageTemplate}
# end

task :all do
  ruby %{setup.rb config}
  ruby %{setup.rb setup}
  ruby %{setup.rb install}
end

task :default => [ :all ]

task :install => [ :all ]

task :clean do
  ruby %{setup.rb clean}
end

require 'rake/rdoctask'
require 'yaml'
Rake::RDocTask.new do |rdoc|
  if File.exist?('VERSION.yml')
    config = YAML::load(File.read('VERSION.yml'))
    version = "#{config[:major]}.#{config[:minor]}.#{config[:patch]}"
  else
    version = ""
  end

  rdoc.rdoc_dir = 'rdoc'
  rdoc.title = "RubyFuse #{version}"
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('lib/**/*.rb')
end
