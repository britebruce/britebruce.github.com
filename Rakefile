require 'jekyll'

options = Jekyll.configuration({})
site    = Jekyll::Site.new(options)
site.read_posts('')

namespace "categories" do
  desc "Generate tag pages"
  task :generate_pages do
    folder = "categories"

    site.categories.each do |categories, posts|
      tag_page = "#{folder}/#{categories}.html"
      tag_page = tag_page.downcase

      File.open(tag_page, 'w') do |file|
        file.write <<-EOS
---
layout: categories
title: "Recology --> posts tagged with #{categories}"
name: #{categories}
---

<div class="article_list">
  {% for post in site.categories.#{categories} %}  
    {% include a_post.html %}
  {% endfor %}
</div>
        EOS
      end
    end
  end
end