<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Juncture-Style Story</title>
  <style>
    body {
      margin: 0;
      font-family: 'Georgia', serif;
      background-color: #fdfdfd;
      color: #111;
    }
    nav {
      background-color: #444;
      color: #fff;
      padding: 1em 2em;
      font-family: sans-serif;
      display: flex;
      gap: 2em;
    }
    .container {
      display: grid;
      grid-template-columns: 4fr 1fr;
      padding: 2em;
      max-width: 1000px;
      margin: auto;
      gap: 2em;
    }
    .narrative p {
      margin-bottom: 3em;
      font-size: 1.2em;
      line-height: 1.7;
    }
    .annotation {
      position: sticky;
      top: 2em;
      background: #f2f2f2;
      padding: 1em;
      border-left: 3px solid #aaa;
      font-size: 0.95em;
      font-style: italic;
    }
    .annotation.hidden {
      visibility: hidden;
      height: 1em;
    }
  </style>
</head>
<body>
  <nav>
    <div>Home</div>
    <div>Contact</div>
  </nav>

  <div class="container">
    <div class="narrative">
      <p data-note="Single. (adj) only one; not one of several.">
        Hello, this is the example of a single column.
      </p>
      <p data-note="Two. (number) equivalent to the sum of one and one; one less than three; 2.">
        One column okay, but two is better!
      </p>
      <p data-note="">
        Keep reading to learn more...
      </p>
    </div>
    <div class="annotation" id="annotation-box"></div>
  </div>

  <script>
    const annotationBox = document.getElementById("annotation-box");
    const paragraphs = document.querySelectorAll(".narrative p");

    function updateAnnotation() {
      let found = false;
      for (let i = 0; i < paragraphs.length; i++) {
        const rect = paragraphs[i].getBoundingClientRect();
        if (rect.top >= 0 && rect.top < window.innerHeight / 2) {
          const note = paragraphs[i].dataset.note;
          if (note) {
            annotationBox.textContent = note;
            annotationBox.classList.remove("hidden");
          } else {
            annotationBox.textContent = "";
            annotationBox.classList.add("hidden");
          }
          found = true;
          break;
        }
      }
      if (!found) {
        annotationBox.textContent = "";
        annotationBox.classList.add("hidden");
      }
    }

    window.addEventListener("scroll", updateAnnotation);
    window.addEventListener("load", updateAnnotation);
  </script>
</body>
</html>
