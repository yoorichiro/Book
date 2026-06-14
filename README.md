<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>No Title</title>
  <style>
    body {
      margin: 0;
      font-family: "Times New Roman", serif;
      background: url('rainy-background.jpg') no-repeat center center fixed;
      background-size: cover;
      color: #2c2c2c;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }

    .book {
      width: 600px;
      height: 800px;
      background: url('medieval-cover-texture.jpg') no-repeat center center;
      background-size: cover;
      box-shadow: 0 0 30px rgba(0,0,0,0.7);
      padding: 40px;
      overflow: hidden;
      position: relative;
      perspective: 1500px; /* enables 3D flip */
    }

    .page {
      display: none;
      font-size: 18px;
      line-height: 1.6;
      transform-origin: left center;
      transition: transform 0.8s ease, opacity 0.8s ease;
      position: absolute;
      top: 40px;
      left: 40px;
      right: 40px;
      bottom: 60px;
      background: rgba(255,255,255,0.85);
      padding: 20px;
      box-shadow: inset 0 0 10px rgba(0,0,0,0.3);
    }

    .page.active {
      display: block;
      transform: rotateY(0deg);
      opacity: 1;
    }

    .page.flip-out {
      transform: rotateY(-90deg);
      opacity: 0;
    }

    .page.flip-in {
      transform: rotateY(90deg);
      opacity: 0;
    }

    .nav-buttons {
      position: absolute;
      bottom: 20px;
      width: 100%;
      text-align: center;
    }

    button {
      background-color: #4a3c2a;
      color: #fff;
      border: none;
      padding: 10px 20px;
      margin: 0 10px;
      cursor: pointer;
      font-family: "Times New Roman", serif;
      font-size: 16px;
    }

    button:hover {
      background-color: #6a543a;
    }
  </style>
</head>
<body>
  <div class="book">
    <div class="page active" id="page0"></div>
    <div class="page" id="page1">yeah i already notice you lost your feelings...</div>
    <div class="page" id="page2">just to let you know, I'll only mention...</div>
    <div class="page" id="page3">During our second week or 4th week...</div>
    <div class="page" id="page4">And naka bantay ko nimo pag every time...</div>
    <div class="page" id="page5">Kato sd gani time imo ko gi inon nga di ka satisfied...</div>
    <div class="page" id="page6">I’ve spent time reflecting on all of this...</div>

    <div class="nav-buttons">
      <button onclick="prevPage()">Previous</button>
      <button onclick="nextPage()">Next</button>
    </div>
  </div>

  <script>
    let currentPage = 0;
    const pages = document.querySelectorAll('.page');

    function showPage(index, direction) {
      const oldPage = pages[currentPage];
      const newPage = pages[index];

      if (direction === 'next') {
        oldPage.classList.add('flip-out');
        setTimeout(() => {
          oldPage.classList.remove('active', 'flip-out');
          newPage.classList.add('active', 'flip-in');
          setTimeout(() => newPage.classList.remove('flip-in'), 50);
        }, 800);
      } else {
        oldPage.classList.add('flip-in');
        setTimeout(() => {
          oldPage.classList.remove('active', 'flip-in');
          newPage.classList.add('active', 'flip-out');
          setTimeout(() => newPage.classList.remove('flip-out'), 50);
        }, 800);
      }
    }

    function nextPage() {
      if (currentPage < pages.length - 1) {
        showPage(currentPage + 1, 'next');
        currentPage++;
      }
    }

    function prevPage() {
      if (currentPage > 0) {
        showPage(currentPage - 1, 'prev');
        currentPage--;
      }
    }
  </script>
</body>
</html>
