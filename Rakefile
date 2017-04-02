require 'rake-jekyll'
require 'html-proofer'
require 'scss_lint/rake_task'
Rake::Jekyll::GitDeployTask.new(:deploy)

task :default => [:lint]

SCSSLint::RakeTask.new do |t|
  t.config = '_config.yml'
  t.files = Dir.glob(['src/_sass/**/*.scss', '!src/_sass/_syntax-highlighting.scss'])
end

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
  Rake::Task["scss_lint"].invoke
  HTMLProofer.check_directory("./_site", {:only_4xx => true}).run
end
