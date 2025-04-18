# R-tsel
<!DOCTYPE html>
<html lang="de">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Rätsel für meinen Lieblingsmenschen ❤️</title>
  <style>
    body {
      font-family: 'Comic Sans MS', cursive, sans-serif;
      background: linear-gradient(135deg, #ffe6f0, #fff0f5);
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      margin: 0;
    }
    .card {
      background: white;
      padding: 2rem;
      border-radius: 20px;
      box-shadow: 0 0 25px rgba(0,0,0,0.1);
      max-width: 500px;
      text-align: center;
    }
    .question {
      font-size: 1.3rem;
      margin-bottom: 1rem;
    }
    input[type="text"] {
      padding: 0.5rem;
      font-size: 1.1rem;
      border: 2px solid #ccc;
      border-radius: 8px;
      text-align: center;
    }
    button {
      margin-top: 1rem;
      padding: 0.5rem 1rem;
      font-size: 1rem;
      border: none;
      background-color: #ff69b4;
      color: white;
      border-radius: 8px;
      cursor: pointer;
    }
    .progress {
      font-size: 1.5rem;
      margin-top: 1rem;
      letter-spacing: 0.3rem;
    }
    .result {
      font-size: 1.4rem;
      color: #008000;
      margin-top: 1rem;
    }
  </style>
</head>
<body>
  <div class="card">
    <h1>💕 Liebesrätsel 💕</h1>
    <p class="question" id="frage"></p>
    <input type="text" id="antwort" maxlength="1">
    <br>
    <button onclick="pruefen()">Antworten</button>
    <div class="result" id="meldung"></div>
    <p class="progress" id="fortschritt"></p>
  </div>

  <script>
    const fragen = [
      { frage: "Welcher Buchstabe kommt nach A?", loesung: "B" },
      { frage: "Welches ist der 5. Buchstabe im Alphabet?", loesung: "E" },
      { frage: "Welcher Buchstabe steckt in 'Sonne' und 'Süß'?", loesung: "S" },
      { frage: "Ich bin der erste Buchstabe in 'Teddy'", loesung: "T" },
      { frage: "Dein Spitzname für mich beginnt mit...? ❤️", loesung: "B" },
      { frage: "Ich bin rund und komme in 'Obst' vor", loesung: "O" },
      { frage: "Der englische Buchstabe, der wie 'why' klingt", loesung: "Y" },
      { frage: "Ich bin der erste Buchstabe in 'Freund'", loesung: "F" },
      { frage: "Welcher Buchstabe kommt nach Q?", loesung: "R" },
      { frage: "Ich bin ein gerader Strich im Alphabet", loesung: "I" },
      { frage: "Ich bin der häufigste Buchstabe in deutschen Wörtern", loesung: "E" },
      { frage: "Ich bin in 'Nacht' und 'Nase'", loesung: "N" },
      { frage: "Ich bin der letzte Buchstabe in 'Hund'", loesung: "D" }
    ];

    let index = 0;
    let ergebnis = Array(fragen.length).fill("_");

    function zeigeFrage() {
      document.getElementById('frage').textContent = fragen[index].frage;
      document.getElementById('fortschritt').textContent = ergebnis.join(" ");
      document.getElementById('antwort').value = "";
      document.getElementById('meldung').textContent = "";
    }

    function pruefen() {
      const eingabe = document.getElementById('antwort').value.toUpperCase();
      const loesung = fragen[index].loesung;

      if (eingabe === loesung) {
        ergebnis[index] = loesung;
        index++;
        if (index < fragen.length) {
          zeigeFrage();
        } else {
          document.getElementById('frage').textContent = "🎉 Du hast das Rätsel gelöst!";
          document.getElementById('meldung').textContent = "Lösungswort: BEST BOYFRIEND 💘";
          document.getElementById('fortschritt').textContent = ergebnis.join(" ");
          document.getElementById('antwort').style.display = 'none';
        }
      } else {
        document.getElementById('meldung').textContent = "Hmm, das stimmt noch nicht. Versuch's nochmal! 😊";
      }
    }

    zeigeFrage();
  </script>
</body>
</html>
