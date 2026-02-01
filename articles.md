---
layout: default
title: Articles
permalink: /articles.html
---

<section class="space-y-24">
    {% if site.posts.size == 0 %}
        <article>
            <p class="text-gray-500">아직 작성된 글이 없습니다.</p>
        </article>
    {% else %}
        {% for post in site.posts %}
            <article class="group cursor-pointer">
                <a href="{{ post.url | relative_url }}">
                    <div class="flex flex-col space-y-3">
                        <h2 class="text-2xl font-semibold leading-snug group-hover:underline underline-offset-4 decoration-1">
                            {{ post.title }}
                        </h2>
                        <p class="text-gray-500 leading-relaxed max-w-2xl">
                            {% if post.excerpt %}
                                {{ post.excerpt | strip_html | truncate: 200 }}
                            {% else %}
                                {{ post.content | strip_html | truncate: 200 }}
                            {% endif %}
                        </p>
                    </div>
                </a>
            </article>
        {% endfor %}
    {% endif %}
</section>
