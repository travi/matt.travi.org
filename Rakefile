require 'rake-jekyll'

def run(command)
    raise "Failed to execute '#{command}'" if !system(command)
end

Rake::Jekyll::GitDeployTask.new(:deploy) do |t|
    # Run this command to build the site.
    t.jekyll_build = ->(dest_dir) {
        run("cd src/")
        run("bundle exec jekyll build --destination #{dest_dir}")
    }
end
