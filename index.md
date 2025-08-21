---
layout: home
title: BeOps - Best Practices for DevOps and SRE
permalink: /
---

# BeOps - Best Practices for DevOps and SRE

Welcome to BeOps, your comprehensive resource for DevOps best practices, Kubernetes deep dives, and Site Reliability Engineering (SRE) principles.

## 🚀 Latest Posts

{% raw %}{% for post in site.posts limit:5 %}
### [{{ post.title }}]({{ post.url }})
**{{ post.date | date: "%B %d, %Y" }}** - {{ post.category | capitalize }}

{{ post.excerpt | strip_html | truncatewords: 30 }}

{% endfor %}{% endraw %}

## 📚 Categories

- **[DevOps](/devops/)** - Best practices and methodologies
- **[Kubernetes](/k8s/)** - Container orchestration and management
- **[SRE](/sre/)** - Site Reliability Engineering principles

## 🔗 Quick Links

- [About](/pages/about/) - Learn more about BeOps
- [Contact](/pages/contact/) - Get in touch
- [RSS Feed](/feed.xml) - Subscribe to updates
