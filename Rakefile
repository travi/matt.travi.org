require 'rake-jekyll'
require 'html/proofer'

Rake::Jekyll::GitDeployTask.new(:deploy)

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
