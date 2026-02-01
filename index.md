---
layout: default
title: About Me
---

<article>
    <div class="space-y-8">
        <div>
            <h1 class="text-4xl font-semibold leading-tight mb-6">안녕하세요</h1>
            <p class="text-gray-500 leading-relaxed text-lg">
                개발과 디자인에 관심이 있는 개발자입니다.
            </p>
        </div>

        <div class="space-y-6 pt-8">
            <section>
                <h2 class="text-2xl font-semibold mb-4">소개</h2>
                <p class="text-gray-500 leading-relaxed">
                    웹 개발과 사용자 경험에 관심이 많습니다. 깔끔하고 미니멀한 디자인을 선호하며, 
                    의미 있는 코드와 콘텐츠를 만드는 것을 좋아합니다.
                </p>
            </section>

            <section>
                <h2 class="text-2xl font-semibold mb-4">연락처</h2>
                <ul class="space-y-2 text-gray-500">
                    <li>
                        <a href="mailto:{{ site.email }}" class="hover:text-black transition-colors">
                            {{ site.email }}
                        </a>
                    </li>
                    <li>
                        <a href="https://github.com/{{ site.github_username }}" target="_blank" class="hover:text-black transition-colors">
                            GitHub
                        </a>
                    </li>
                    <li>
                        <a href="https://www.linkedin.com/in/{{ site.linkedin_username }}" target="_blank" class="hover:text-black transition-colors">
                            LinkedIn
                        </a>
                    </li>
                </ul>
            </section>
        </div>
    </div>
</article>
