<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Markdown with Sticky Comments</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
    }
    nav {
      background-color: #444;
      color: white;
      padding: 1em;
      display: flex;
      justify-content: flex-start;
      gap: 2em;
    }
    .container {
      display: grid;
      grid-template-columns: 80% 20%;
      padding: 2em;
      gap: 1em;
    }
    .markdown {
      font-size: 1.2em;
      line-height: 1.6;
    }
    .markdown p {
      margin-bottom: 2em;
      position: relative;
    }
    .comments {
      position: sticky;
      top: 2em;
      font-size: 0.9em;
      color: #333;
      border-left: 2px solid #ccc;
      padding-left: 1em;
    }
    .comment-block {
      margin-bottom: 4em;
    }
    .comment-title {
      font-weight: bold;
    }
  </style>
</head>
<body>
  <nav>
    <div>Home</div>
    <div>Contact</div>
  </nav>

  <div class="container">
    <div class="markdown" id="markdown-content"></div>
    <div class="comments">
      <div class="comment-block">
        <div class="comment-title">"Hello, this is the example of a single column."</div>
        <div>Single. (adj) only one; not one of several.</div>
      </div>
      <div class="comment-block">
        <div class="comment-title">"One column okay, but two is better!"</div>
        <div>Two. (number) equivalent to the sum of one and one; one less than three; 2.</div>
      </div>
    </div>
  </div>

  <!-- Load Marked.js for Markdown parsing -->
  <script src="https://cdn.jsdelivr.net/npm/marked/marked.min.js"></script>
  <script>
    const markdownText = `
Hello, this is the example of a single column.  
One column okay, but two is better!  
Keep reading to learn more...
    `;
    document.getElementById('markdown-content').innerHTML = marked.parse(markdownText);
  </script>
</body>
</html>
