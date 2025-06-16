---
title: **Queen's pass** <img src="images/hollow-knight.png" alt="Logo" width="8" height="8" />

---
<h2>最新信息</h2>

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a> - {{ post.date | date: "%Y-%m-%d" }}
    </li>
  {% endfor %}
</ul>

## 🦠🔬🧬🧫

<div class="word-cloud">
  {% for word in site.highlight_words %}
    <span class="cloud-word cloud-word-{{ forloop.index }}">{{ word }}</span>
  {% endfor %}
</div>

<style>
.word-cloud {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  padding: 1rem;
  max-width: 800px;
}

.cloud-word {
  display: inline-block;
  font-family: "Comic Sans MS", cursive, sans-serif;
  font-weight: bold;
  transition: transform 0.3s, color 0.3s;
}

.cloud-word:hover {
  transform: scale(1.2) rotate(5deg);
  color: #e63946;
}

/* 不同词语用 nth-child 来随机大小和颜色 */
.cloud-word-1 {
  font-size: 2rem;
  color: #007acc;
}
.cloud-word-2 {
  font-size: 1.5rem;
  color: #d6336c;
}
.cloud-word-3 {
  font-size: 2.2rem;
  color: #2a9d8f;
}
.cloud-word-4 {
  font-size: 1.8rem;
  color: #f4a261;
}
.cloud-word-5 {
  font-size: 2.4rem;
  color: #e76f51;
}
.cloud-word-6 {
  font-size: 1.6rem;
  color: #264653;
}
  .cloud-word-7 {
  font-size: 1.9rem;
  color: #256653;
}
  .cloud-word-8 {
  font-size: 1.6rem;
  color: #266465;
}
  .cloud-word-9 {
  font-size: 2.6rem;
  color: #267853;
}
  .cloud-word-10 {
  font-size: 2.6rem;
  color: #264653;
}
</style>
