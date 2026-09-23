# Jitter og JavaScript

Animation af en Jitter-json fil via JavaScript. Virker det?

----

## Ideer fra Claude Haiku

Denne tutorial er lavet med lidt hjælp fra Claude AI på DuckDuckGo. Claude er ikke så god til dansk, og den blander de skandinaviske sprog sammen ...

### Eksport fra Jitter/Figma

Når du eksporterer din JSON må der ikke være mellemrum til filnavnet. Danske specialtegn bør også undgås. 

Jeg måtte omdøbe fra: `Jitter Frame 1.json` til `jitterframe.json`. Så virkede koden.

Så undgå mellemrum i filnavnet.

### HTML

Indsæt dette script i filens `<head>` afdeling:

~~~~ 
<script src="https://cdnjs.cloudflare.com/ajax/libs/bodymovin/5.10.2/lottie.min.js"></script>
~~~~

Et passende sted i `<body>` skal der være en HTML-container til animationen:

~~~~
<div id="jitter-container"></div>
~~~~



### JavaScript

~~~~
const animation = lottie.loadAnimation({
  container: document.getElementById('jitter-container'),
  renderer: 'svg',
  loop: true,
  autoplay: true,
  path: 'jitterframe.json' // Stien til din jitter-json fil
});
~~~~

### Eksempel: Knapper

Claude tror, at jeg er svensker, og prøver at svare med sit noget vingeskudte kendskab til skandinaviske sprog. 

~~~~
<div id="jitter-container"></div>

<button id="play-btn">Spill</button>
<button id="pause-btn">Pause</button>
<button id="stop-btn">Stopp</button>

<script src="https://cdnjs.cloudflare.com/ajax/libs/bodymovin/5.10.2/lottie.min.js"></script>

<script>
  const animation = lottie.loadAnimation({
    container: document.getElementById('jitter-container'),
    renderer: 'svg',
    loop: true,
    autoplay: false, // Start ikke automatisk
    path: 'jitterframe.json'
  });

  // Knappekontroller
  document.getElementById('play-btn').addEventListener('click', () => {
    animation.play();
  });

  document.getElementById('pause-btn').addEventListener('click', () => {
    animation.pause();
  });

  document.getElementById('stop-btn').addEventListener('click', () => {
    animation.stop();
  });
</script>
~~~~
