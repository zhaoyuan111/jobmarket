---
layout: page 
---
<!-- 用HTML写标题，插入小logo -->
<h1>
  <img src="images/hollow-knight.png" alt="Logo" width="35" height="35" />
  Queen's Pass
</h1>

<button onclick="location.href='/jobmarket/story1/'" style="
  padding: 10px 20px;
  font-size: 18px;
  background: #007acc;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
">
  请点我一下！
</button>

{% for post in site.posts %}
  <h2 class="post-title">
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
  </h2>
{% endfor %}

<style>
body {
  font-family: "Centaur", cursive, sans-serif;
  font-size: 32px;
}
</style>
<style>
  .post-title {
    font-family: 'FangSong', cursive;
    color: #333;
    font-size: 32px;
  }
</style>
<h2>📅</h2>

<div>
  <button onclick="changeMonth(-1)">« 上一月</button>
  <button onclick="changeMonth(1)">下一月 »</button>
</div>

<div id="calendar"></div>

<script>
  const events = [
    {% for item in site.data.events %}
      {
        date: "{{ item.date }}",
        title: "{{ item.title }}",
        link: "{{ item.link }}"
      },
    {% endfor %}
  ];

  const calendar = document.getElementById("calendar");
  let current = new Date();

  function renderCalendar(y, m) {
    calendar.innerHTML = "";
    const date = new Date(y, m, 1);
    const days = ["Sun","Mon","Tue","Wed","Thu","Fri","Sat"];
    let html = `<h3>${y} 年 ${m+1} 月</h3>`;
    html += "<table><tr>";
    days.forEach(d => html += "<th>" + d + "</th>");
    html += "</tr><tr>";
    for(let i=0; i<date.getDay(); i++) html += "<td></td>";
    while(date.getMonth() === m) {
      const day = date.getDate();
      const dateString = `${y}-${String(m+1).padStart(2,'0')}-${String(day).padStart(2,'0')}`;
      const found = events.find(e => e.date === dateString);
      if(found){
        html += `<td style="background: #ffd; cursor:pointer;" onclick="showEvent('${found.title}', '${found.link}')">${day}</td>`;
      } else {
        html += `<td>${day}</td>`;
      }
      if(date.getDay() === 6) html += "</tr><tr>";
      date.setDate(day + 1);
    }
    html += "</tr></table>";
    calendar.innerHTML = html;
  }

  function showEvent(title, link) {
    if(confirm(title + "\\n点击确定查看详情")) {
      window.location.href = link;
    }
  }

  function changeMonth(offset) {
    current.setMonth(current.getMonth() + offset);
    renderCalendar(current.getFullYear(), current.getMonth());
  }

  renderCalendar(current.getFullYear(), current.getMonth());
</script>

<style>
  #calendar table {
    border-collapse: collapse;
    margin: 20px 0;
  }
  #calendar th, #calendar td {
    border: 1px solid #ccc;
    padding: 8px;
    text-align: center;
    width: 40px;
    height: 40px;
  }
  button {
    margin: 5px;
    padding: 6px 12px;
    cursor: pointer;
  }
</style>

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


<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>生日快乐!</title>
  <style>
    body {
      font-family: 'Arial', sans-serif;
      margin: 0;
      background-color: #ffe6f0;
    }

    /* 背景遮罩 */
    #popup-overlay {
      position: fixed;
      top: 0; left: 0;
      width: 100%; height: 100%;
      background: rgba(0,0,0,0.5);
      display: flex;
      align-items: center;
      justify-content: center;
      z-index: 999;
    }

    /* 弹出框 */
    #birthday-popup {
      background: white;
      border-radius: 20px;
      padding: 30px;
      text-align: center;
      box-shadow: 0 0 20px rgba(0,0,0,0.2);
      max-width: 400px;
      animation: popupFadeIn 1s ease;
      position: relative;
    }

    @keyframes popupFadeIn {
      from { transform: scale(0.5); opacity: 0; }
      to { transform: scale(1); opacity: 1; }
    }

    #birthday-popup h1 {
      color: #ff4081;
      margin-bottom: 15px;
    }

    #birthday-popup img {
      width: 100px;
      height: auto;
      margin: 10px 0;
    }

    #birthday-popup button {
      margin-top: 20px;
      padding: 10px 20px;
      background: #ff4081;
      color: white;
      border: none;
      border-radius: 10px;
      font-size: 16px;
      cursor: pointer;
    }

    #birthday-popup button:hover {
      background: #e73370;
    }
  </style>
</head>
<body>

<!-- 弹窗 HTML -->
<div id="popup-overlay">
  <div id="birthday-popup">
    <h1>🎉 生日快乐！🎂</h1>
    <img src="https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExemJ4YTBleWNnN3JmY3g3Yjk3YTExbHMzaGpvNXU0cDVuNzMwcXQwbSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/JoOWFsAGWB0L2aSaA1/giphy.gif" alt="Happy Birthday">
    <p>希望今天是开心的一天 🍰</p>
    <button onclick="closePopup()">Music！</button>
  </div>
</div>


<button onclick="playMusic(); closePopup()">Music！</button>

<script>
  function playMusic() {
    const audio = new Audio('https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3');
    audio.play();
  }

  function closePopup() {
    document.getElementById("popup-overlay").style.display = "none";
  }
</script>

