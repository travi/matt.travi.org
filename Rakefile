require 'rake-jekyll'
require 'html-proofer'
Rake::Jekyll::GitDeployTask.new(:deploy)

task :default => [:lint]

desc 'Generate site from Travis CI and publish to GitHub Pages.'
task :travis do
  Rake::Task["build"].invoke
  Rake::Task["deploy"].invoke
  sh('git checkout master')
end

desc 'Generate front-end dependencies'
task :build do
  sh('grunt build')
end

desc 'Lint the code'
task :lint do
  sh('grunt lint')
  HTMLProofer.check_directory("./_site", {:only_4xx => true}).run
end
