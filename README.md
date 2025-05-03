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
      <ul class="topic-list" id="topicList"></ul>
    </div>
    <div class="content" id="content">
      <!-- Nội dung topic sẽ hiển thị ở đây -->
    </div>
  </div>

  <script>
    let topics = [];

    // Load từ LocalStorage nếu có
    if (localStorage.getItem('ieltsTopics')) {
      topics = JSON.parse(localStorage.getItem('ieltsTopics'));
    } else {
       topics = [
    {
      title: "Topic 1: Accommodation",
      question: "Do you live in a house or an apartment?",
      answer: "I'm currently living with my parents in a two-story house...",
      vocab: "<div class='vocab-box'><p><b>cozy</b>: ấm cúng</p></div>"
    },
    {
      title: "Topic 2: Advertisement",
      question: "Do you like watching advertisements?",
      answer: "Sometimes I do, especially if they are funny or creative.",
      vocab: ""
    },
    {
      title: "Topic 3: Alone",
      question: "Do you like spending time alone?",
      answer: "Yes, I enjoy being alone from time to time.",
      vocab: ""
    },
    {
      title: "Topic 4: Music",
      question: "Do you enjoy listening to music?",
      answer: "Yes, I absolutely love music. It's a big part of my daily life.",
      vocab: ""
    },
    {
      title: "Topic 5: Travel",
      question: "Do you like traveling?",
      answer: "Yes, I love traveling. It allows me to explore new cultures.",
      vocab: ""
    },
    {
      title: "Topic 6: Food",
      question: "What kind of food do you like?",
      answer: "I enjoy a variety of foods, especially Vietnamese and Italian dishes.",
      vocab: ""
    },
    {
      title: "Topic 7: Weather",
      question: "What kind of weather do you like?",
      answer: "I prefer cool and sunny weather because it's comfortable and uplifting.",
      vocab: ""
    },
    {
      title: "Topic 8: Books",
      question: "Do you like reading books?",
      answer: "Yes, I love reading fiction and self-help books in my free time.",
      vocab: ""
    },
    {
      title: "Topic 9: Hobbies",
      question: "What are your hobbies?",
      answer: "My hobbies include drawing, reading and playing badminton.",
      vocab: ""
    },
    {
      title: "Topic 10: Daily Routine",
      question: "What is your typical daily routine?",
      answer: "I usually wake up at 6 a.m., exercise, then go to school or work.",
      vocab: ""
    }
  ];
    }

    const contentDiv = document.getElementById('content');
    const topicList = document.getElementById('topicList');

    function renderTopicList() {
      topicList.innerHTML = '';
      topics.forEach((topic, index) => {
        const li = document.createElement('li');
        li.textContent = topic.title || `Topic ${index + 1}`;
        li.onclick = () => showTopic(index);
        topicList.appendChild(li);
      });
    }

    function showTopic(index) {
      const topic = topics[index];
      contentDiv.innerHTML = `
        <h1>${topic.title || 'Enter Your Topic Details'}</h1>
        <label>Title</label>
        <input type="text" id="title" value="${topic.title}">
        <label>Question</label>
        <input type="text" id="question" value="${topic.question}">
        <label>Answer</label>
        <textarea id="answer">${topic.answer}</textarea>
        <label>Vocabulary</label>
        <textarea id="vocab">${topic.vocab}</textarea>
        <button onclick="saveTopic(${index})">Save Topic</button>
        <button onclick="addNewTopic()">+ Add New Topic</button>
      `;

      // Highlight active
      document.querySelectorAll('.topic-list li').forEach((li, i) => {
        li.classList.toggle('active', i === index);
      });
    }

    function saveTopic(index) {
      topics[index] = {
        title: document.getElementById('title').value,
        question: document.getElementById('question').value,
        answer: document.getElementById('answer').value,
        vocab: document.getElementById('vocab').value
      };
      localStorage.setItem('ieltsTopics', JSON.stringify(topics));
      renderTopicList();
      showTopic(index);
    }

    function addNewTopic() {
      topics.push({ title: '', question: '', answer: '', vocab: '' });
      localStorage.setItem('ieltsTopics', JSON.stringify(topics));
      renderTopicList();
      showTopic(topics.length - 1);
    }

    // Khởi động
    renderTopicList();
    showTopic(0);
  </script>
</body>
</html>
