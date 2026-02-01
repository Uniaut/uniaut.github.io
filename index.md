---
layout: default
title: About Me
---

<article>
    <div class="space-y-8">
        <div>
            <h1 class="text-4xl font-semibold leading-tight mb-6">안녕하세요, 최건우입니다.</h1>
            <p class="text-gray-500 leading-relaxed text-lg">
                LLM enthausiast (아님)
                Crypto enthausiast (더더욱 아님)
                삼성전자에서 native S/W를 개발하고 있습니다.
            </p>
        </div>

        <div class="space-y-6 pt-8">
            <section>
                <h2 class="text-2xl font-semibold mb-4">Career</h2>
                <p class="text-gray-500 leading-relaxed">
                    24.07 ~ 삼성전자 (S/W engineer)
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
