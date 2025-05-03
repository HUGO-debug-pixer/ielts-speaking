<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>IELTS Speaking Part 1 - Custom Topics</title>
  <style>
    body { margin: 0; font-family: Arial, sans-serif; }
    .container { display: flex; height: 100vh; }
    .sidebar {
      width: 250px;
      background: #f0f0f0;
      border-right: 1px solid #ccc;
      overflow-y: auto;
      padding: 1rem;
    }
    .sidebar h2 { font-size: 18px; margin-bottom: 1rem; }
    .topic-list { list-style: none; padding: 0; }
    .topic-list li {
      padding: 8px 12px;
      cursor: pointer;
      border-radius: 4px;
    }
    .topic-list li:hover { background: #d0e8ff; }
    .active { background: #90caf9; font-weight: bold; }
    .content {
      flex: 1;
      padding: 2rem;
      overflow-y: auto;
    }
    .vocab-box {
      border: 1px solid #ccc;
      padding: 10px;
      margin-top: 1rem;
    }
    input, textarea { width: 100%; padding: 10px; margin: 10px 0; }
  </style>
</head>
<body>
  <div class="container">
    <div class="sidebar">
      <h2>IELTS SPEAKING PART 1</h2>
      <ul class="topic-list" id="topicList">
        <li onclick="showTopic(0)" class="active">Topic 1: Accommodation</li>
        <li onclick="showTopic(1)">Topic 2: Advertisement</li>
        <li onclick="showTopic(2)">Topic 3: Alone</li>
        <li onclick="showTopic(3)">Topic 4: Music</li>
        <li onclick="showTopic(4)">Topic 5: Travel</li>
      </ul>
    </div>
    <div class="content" id="content">
      <h1>Enter Your Topic Details</h1>
      <label for="title">Title</label>
      <input type="text" id="title" placeholder="Enter the topic title">
      <label for="question">Question</label>
      <input type="text" id="question" placeholder="Enter the question">
      <label for="answer">Answer</label>
      <textarea id="answer" placeholder="Enter your answer"></textarea>
      <label for="vocab">Vocabulary</label>
      <textarea id="vocab" placeholder="Enter vocabulary and meanings"></textarea>
      <button onclick="saveTopic()">Save Topic</button>
    </div>
  </div>

  <script>
    const topics = [
      {
        title: "Topic 1: Accommodation",
        question: "Do you live in a house or an apartment?",
        answer: `I'm currently living with my parents in a two-story house in the middle of the city. It's quite small but very <b style='color:red;'>cozy</b>. It has a spacious living room, three bedrooms, three bathrooms and an <b style='color:red;'>open-plan kitchen</b>. There's a lovely garden on the top floor where we usually have <b style='color:red;'>barbecues</b> at the weekend and <b style='color:red;'>enjoy the fantastic view</b> of the city.`,
        vocab: `
          <div class='vocab-box'>
            <p><b>cozy</b>: ấm cúng - warm, comfortable and safe</p>
            <p><b>open-plan kitchen</b>: nhà bếp không gian mở</p>
            <p><b>barbecues</b>: tiệc nướng</p>
            <p><b>enjoy the fantastic view</b>: tận hưởng khung cảnh tuyệt vời</p>
          </div>`
      },
      {
        title: "Topic 2: Advertisement",
        question: "Do you like watching advertisements?",
        answer: "Sometimes I do, especially if they are funny or creative. I think good advertisements can be entertaining and even inspiring.",
        vocab: ""
      },
      {
        title: "Topic 3: Alone",
        question: "Do you like spending time alone?",
        answer: "Yes, I enjoy being alone from time to time. It gives me a chance to relax and think without distractions.",
        vocab: ""
      },
      {
        title: "Topic 4: Music",
        question: "Do you enjoy listening to music?",
        answer: "Yes, I absolutely love music. It's a big part of my daily life, and I listen to it whenever I can. I enjoy different genres, but my favorites are pop and classical music.",
        vocab: `
          <div class='vocab-box'>
            <p><b>genre</b>: thể loại - a style or category of art, music, or literature</p>
            <p><b>pop music</b>: nhạc pop - popular music</p>
            <p><b>classical music</b>: nhạc cổ điển</p>
          </div>`
      },
      {
        title: "Topic 5: Travel",
        question: "Do you like traveling?",
        answer: "Yes, I love traveling. It allows me to experience new cultures, meet interesting people, and explore different parts of the world. I try to travel whenever I have the opportunity.",
        vocab: `
          <div class='vocab-box'>
            <p><b>cultures</b>: văn hóa - the customs, art, social institutions, and achievements of a particular nation, people, or other social group</p>
            <p><b>explore</b>: khám phá - to travel around a place in order to learn about it</p>
          </div>`
      }
    ];

    const contentDiv = document.getElementById('content');
    const topicListItems = document.querySelectorAll('.topic-list li');
    
    function showTopic(index) {
      const topic = topics[index] || {title: '', question: '', answer: '', vocab: ''};
      contentDiv.innerHTML = `
        <h1>${topic.title || 'Enter Your Topic Details'}</h1>
        <label for="title">Title</label>
        <input type="text" id="title" value="${topic.title || ''}" placeholder="Enter the topic title">
        <label for="question">Question</label>
        <input type="text" id="question" value="${topic.question || ''}" placeholder="Enter the question">
        <label for="answer">Answer</label>
        <textarea id="answer" placeholder="Enter your answer">${topic.answer || ''}</textarea>
        <label for="vocab">Vocabulary</label>
        <textarea id="vocab" placeholder="Enter vocabulary and meanings">${topic.vocab || ''}</textarea>
        <button onclick="saveTopic(${index})">Save Topic</button>
      `;
    }

    function saveTopic(index) {
      const title = document.getElementById('title').value;
      const question = document.getElementById('question').value;
      const answer = document.getElementById('answer').value;
      const vocab = document.getElementById('vocab').value;

      if (index !== undefined) {
        topics[index] = {title, question, answer, vocab};
      } else {
        topics.push({title, question, answer, vocab});
      }

      updateTopicList();
    }

    function updateTopicList() {
      const topicList = document.getElementById('topicList');
      topicList.innerHTML = '';
      topics.forEach((topic, index) => {
        const li = document.createElement('li');
        li.textContent = topic.title || `Topic ${index + 1}`;
        li.onclick = () => showTopic(index);
        topicList.appendChild(li);
      });
    }

    // Hiển thị chủ đề đầu tiên khi trang load
    showTopic(0);
  </script>
</body>
</html>
