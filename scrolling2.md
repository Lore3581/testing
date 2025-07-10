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
  <div class="container">
    <div class="narrative">
      <p data-note="Single. (adj) only one; not one of several.">
        Hello, this is the example of a single column. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin vitae cursus arcu. Ut venenatis massa ut nibh porta, ac porttitor lacus mollis. Nulla facilisi. Praesent laoreet ex ante, eu lacinia sem varius in. Nulla molestie ligula nisl, at lacinia lorem tempus at. Proin laoreet feugiat condimentum. Aliquam in enim lectus. Aenean ut purus id tellus tincidunt rhoncus. Pellentesque cursus fringilla maximus. In ultrices arcu ut velit convallis rutrum. In eleifend euismod libero, finibus convallis nisi.

Aliquam a lacinia est. Sed eu imperdiet augue. Etiam tincidunt hendrerit ex, quis faucibus nunc commodo non. Suspendisse ac nulla justo. Nulla luctus purus sed ornare semper. Etiam nec hendrerit odio. Curabitur eget nulla erat.

Curabitur condimentum, nulla vel interdum malesuada, massa purus efficitur ligula, vitae venenatis neque nisl vitae lacus. Integer vitae lacus commodo, porttitor massa ac, volutpat dui. Donec sed venenatis quam. Maecenas sit amet pulvinar tortor. Aenean ut felis luctus, pulvinar odio et, dapibus neque. Nunc quis mollis lectus. Nunc sit amet orci eget metus dapibus bibendum sed non ligula. Morbi consectetur varius lorem, et pellentesque nulla viverra id. Integer pellentesque efficitur dolor eget tristique. Praesent tincidunt sapien nec massa eleifend, vitae efficitur tortor dictum. Suspendisse nec ante et nunc consectetur aliquet. Etiam dictum erat a arcu tempus, a aliquam nisi rutrum. Morbi tristique ligula lacus, id blandit est dignissim sagittis.
      </p>
      <p data-note="Two. (number) equivalent to the sum of one and one; one less than three; 2.">
        One column okay, but two is better! Mauris vel dictum est, vel venenatis risus. Aenean convallis ornare purus, vel pulvinar nisi egestas a. Etiam interdum arcu id felis egestas aliquam. Aliquam a interdum dolor. Quisque fringilla metus ac libero luctus, ut laoreet mi suscipit. Nam eu lorem risus. Nulla semper dolor et vestibulum iaculis. Donec nec arcu euismod risus porta commodo. Vivamus ut suscipit diam, viverra cursus orci. Sed lectus orci, auctor non turpis ut, fringilla sagittis tortor. Quisque varius, mauris ut ultrices iaculis, purus libero hendrerit arcu, in vestibulum erat massa in felis. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Aliquam tempus risus volutpat, tincidunt nibh sed, iaculis nisl.

Curabitur nec ipsum placerat, pellentesque arcu et, porttitor augue. Sed pellentesque malesuada sapien id venenatis. Fusce mauris nisl, pellentesque consequat tincidunt nec, cursus et libero. Donec molestie tristique ullamcorper. Nunc tincidunt eros sed nibh tincidunt ultricies. Proin consectetur nunc vel maximus imperdiet. Phasellus hendrerit pulvinar hendrerit. Proin augue tellus, commodo sit amet nisi a, imperdiet placerat ligula. Fusce eget tortor et sem posuere consequat. Proin placerat leo sit amet metus volutpat, sit amet gravida mauris condimentum. Duis eros libero, fringilla at mauris in, imperdiet blandit tellus. Quisque finibus ipsum id magna imperdiet rutrum. Morbi pretium quam vel massa tincidunt, vitae efficitur ex imperdiet.
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
