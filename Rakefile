require 'rake-jekyll'
require 'html/proofer'
Rake::Jekyll::GitDeployTask.new(:deploy)

task :default => [:build]

desc 'Generate site from Travis CI and publish to GitHub Pages.'
task :travis do
  Rake::Task["build"].invoke
  Rake::Task["deploy"].invoke
end

desc 'Generate front-end dependencies'
task :build do
  sh('grunt build')
end

desc 'Lint the code'
task :lint do
  HTML::Proofer.new(
    "./_site",
    {
      :href_ignore => ['http://localhost:4000'],
      :href_swap => {
          %r{^/matt.travi.org} => ''
      },
      :verbose => true,
      :check_html => true
    }
  ).run
end
