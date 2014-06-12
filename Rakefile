
task :default => [:build, :serve]

task :build do
  puts `jekyll build`
end

task :serve do
  puts `bundle exec jekyll serve`
end

task :post, :name do |t, args|
  begin
    file_name = "#{Time.now.strftime "%Y-%m-%d"}-#{args[:name].downcase.gsub(/ /, "-")}.md"
    path = File.expand_path("../_posts", __FILE__)

    File.open(File.expand_path(file_name, path), File::WRONLY|File::CREAT|File::EXCL) do |f|
      f.write <<-EOF
---
layout: post
title: #{args[:name]}
---

      EOF
    end

    puts "File '#{file_name}' added to _posts!"
  rescue
    puts "\033[1;31mFile with this name already exists in _posts!"
  end
end
