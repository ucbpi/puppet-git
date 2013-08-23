require 'rake'

exclude_paths = [
  "pkg/**/*.pp",
  "spec/**/*.pp",
]

begin
  require 'rspec/core/rake_task'
  require 'puppet-lint/tasks/puppet-lint'
  PuppetLint.configuration.ignore_paths = exclude_paths
  PuppetLint.configuration.send("disable_80chars")
rescue LoadError
  require 'rubygems'
  retry
end

RSpec::Core::RakeTask.new(:spec) do |t|
  t.pattern = 'spec/*/*_spec.rb'
end

desc "Run lint, syntax and spec testing"
task :default => [:lint,:spec]
