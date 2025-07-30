<!DOCTYPE html>
<html lang="pt">
<head>
  <meta charset="UTF-8">
  <title>EcoDrop – Water Usage</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #e0f7fa;
      color: #1b5e20;
      margin: 0;
      padding: 0;
    }
    header {
      background: linear-gradient(to right, #81d4fa, #a5d6a7);
      padding: 1rem;
      text-align: center;
    }
    h1 {
      margin: 0;
      font-size: 1.8rem;
    }
    main {
      max-width: 700px;
      margin: 2rem auto;
      background: #ffffff;
      border-radius: 20px;
      padding: 2rem;
      box-shadow: 0 0 15px rgba(0,0,0,0.1);
    }
    .icon-box {
      display: flex;
      justify-content: space-around;
      flex-wrap: wrap;
      gap: 1rem;
      margin-bottom: 2rem;
    }
    .icon-item {
      width: 100px;
      height: 100px;
      border-radius: 15px;
      background: #c8e6c9;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 2rem;
      box-shadow: 2px 2px 10px rgba(0,0,0,0.1);
    }
    label, select, input {
      display: block;
      width: 100%;
      margin: 0.5rem 0;
      padding: 0.8rem;
      border-radius: 10px;
      border: 1px solid #ccc;
    }
    button {
      background-color: #26a69a;
      color: #fff;
      padding: 1rem;
      width: 100%;
      border: none;
      font-size: 1rem;
      border-radius: 10px;
      margin-top: 1rem;
      cursor: pointer;
    }
    .result {
      margin-top: 1.5rem;
      background-color: #b2dfdb;
      padding: 1rem;
      border-radius: 10px;
      font-size: 1.2rem;
      text-align: center;
    }
  </style>
</head>
<body>
  <header>
    <h1>EcoDrop – Water Usage</h1>
  </header>

  <main>
    <div class="icon-box">
      <div class="icon-item" title="Banho 🚿">🛁</div>
      <div class="icon-item" title="Descarga 🚽">🚽</div>
      <div class="icon-item" title="Louça 🍽️">🍽️</div>
      <div class="icon-item" title="Torneira 💧">🚰</div>
    </div>

    <label>Banhos por dia</label>
    <input type="number" id="baths" placeholder="Ex: 2">

    <label>Duração do banho (min)</label>
    <input type="number" id="showerTime" placeholder="Ex: 10">

    <label>Descargas por dia</label>
    <input type="number" id="flushes" placeholder="Ex: 5">

    <label>Lavagens de louça por semana</label>
    <input type="number" id="dishwashing" placeholder="Ex: 7">

    <label>Tempo de uso da torneira (min/dia)</label>
    <input type="number" id="faucetTime" placeholder="Ex: 15">

    <label>Escolha o período</label>
    <select id="period">
      <option value="day">Por Dia</option>
      <option value="month" selected>Por Mês</option>
      <option value="year">Por Ano</option>
    </select>

    <button onclick="calculateWater()">Ver Consumo</button>

    <div class="result" id="resultBox"></div>
  </main>

  <script>
    function calculateWater() {
      const baths = +document.getElementById("baths").value || 0;
      const showerTime = +document.getElementById("showerTime").value || 0;
      const flushes = +document.getElementById("flushes").value || 0;
      const dishwashing = +document.getElementById("dishwashing").value || 0;
      const faucetTime = +document.getElementById("faucetTime").value || 0;
      const period = document.getElementById("period").value;

      const showerL = baths * showerTime * 9;
      const flushL = flushes * 6;
      const dishL = (dishwashing / 7) * 15; // convertido pra diário
      const faucetL = faucetTime * 6;

      const dailyTotal = showerL + flushL + dishL + faucetL;

      let multiplier = 1;
      let label = "dia";

      if (period === "month") {
        multiplier = 30;
        label = "mês";
      } else if (period === "year") {
        multiplier = 365;
        label = "ano";
      }

      const final = Math.round(dailyTotal * multiplier);

      document.getElementById("resultBox").innerHTML = 
        `Você consome cerca de <strong>${final} litros</strong> de água por ${label}.`;
    }
  </script>
</body>
</html><!DOCTYPE html>
<html lang="pt">
<head>
  <meta charset="UTF-8">
  <title>EcoDrop – Water Usage</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #e0f7fa;
      color: #1b5e20;
      margin: 0;
      padding: 0;
    }
    header {
      background: linear-gradient(to right, #81d4fa, #a5d6a7);
      padding: 1rem;
      text-align: center;
    }
    h1 {
      margin: 0;
      font-size: 1.8rem;
    }
    main {
      max-width: 700px;
      margin: 2rem auto;
      background: #ffffff;
      border-radius: 20px;
      padding: 2rem;
      box-shadow: 0 0 15px rgba(0,0,0,0.1);
    }
    .icon-box {
      display: flex;
      justify-content: space-around;
      flex-wrap: wrap;
      gap: 1rem;
      margin-bottom: 2rem;
    }
    .icon-item {
      width: 100px;
      height: 100px;
      border-radius: 15px;
      background: #c8e6c9;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 2rem;
      box-shadow: 2px 2px 10px rgba(0,0,0,0.1);
    }
    label, select, input {
      display: block;
      width: 100%;
      margin: 0.5rem 0;
      padding: 0.8rem;
      border-radius: 10px;
      border: 1px solid #ccc;
    }
    button {
      background-color: #26a69a;
      color: #fff;
      padding: 1rem;
      width: 100%;
      border: none;
      font-size: 1rem;
      border-radius: 10px;
      margin-top: 1rem;
      cursor: pointer;
    }
    .result {
      margin-top: 1.5rem;
      background-color: #b2dfdb;
      padding: 1rem;
      border-radius: 10px;
      font-size: 1.2rem;
      text-align: center;
    }
  </style>
</head>
<body>
  <header>
    <h1>EcoDrop – Water Usage</h1>
  </header>

  <main>
    <div class="icon-box">
      <div class="icon-item" title="Banho 🚿">🛁</div>
      <div class="icon-item" title="Descarga 🚽">🚽</div>
      <div class="icon-item" title="Louça 🍽️">🍽️</div>
      <div class="icon-item" title="Torneira 💧">🚰</div>
    </div>

    <label>Banhos por dia</label>
    <input type="number" id="baths" placeholder="Ex: 2">

    <label>Duração do banho (min)</label>
    <input type="number" id="showerTime" placeholder="Ex: 10">

    <label>Descargas por dia</label>
    <input type="number" id="flushes" placeholder="Ex: 5">

    <label>Lavagens de louça por semana</label>
    <input type="number" id="dishwashing" placeholder="Ex: 7">

    <label>Tempo de uso da torneira (min/dia)</label>
    <input type="number" id="faucetTime" placeholder="Ex: 15">

    <label>Escolha o período</label>
    <select id="period">
      <option value="day">Por Dia</option>
      <option value="month" selected>Por Mês</option>
      <option value="year">Por Ano</option>
    </select>

    <button onclick="calculateWater()">Ver Consumo</button>

    <div class="result" id="resultBox"></div>
  </main>

  <script>
    function calculateWater() {
      const baths = +document.getElementById("baths").value || 0;
      const showerTime = +document.getElementById("showerTime").value || 0;
      const flushes = +document.getElementById("flushes").value || 0;
      const dishwashing = +document.getElementById("dishwashing").value || 0;
      const faucetTime = +document.getElementById("faucetTime").value || 0;
      const period = document.getElementById("period").value;

      const showerL = baths * showerTime * 9;
      const flushL = flushes * 6;
      const dishL = (dishwashing / 7) * 15; // convertido pra diário
      const faucetL = faucetTime * 6;

      const dailyTotal = showerL + flushL + dishL + faucetL;

      let multiplier = 1;
      let label = "dia";

      if (period === "month") {
        multiplier = 30;
        label = "mês";
      } else if (period === "year") {
        multiplier = 365;
        label = "ano";
      }

      const final = Math.round(dailyTotal * multiplier);

      document.getElementById("resultBox").innerHTML = 
        `Você consome cerca de <strong>${final} litros</strong> de água por ${label}.`;
    }
  </script>
</body>
</html><!DOCTYPE html>
<html lang="pt">
<head>
  <meta charset="UTF-8">
  <title>EcoDrop – Water Usage</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #e0f7fa;
      color: #1b5e20;
      margin: 0;
      padding: 0;
    }
    header {
      background: linear-gradient(to right, #81d4fa, #a5d6a7);
      padding: 1rem;
      text-align: center;
    }
    h1 {
      margin: 0;
      font-size: 1.8rem;
    }
    main {
      max-width: 700px;
      margin: 2rem auto;
      background: #ffffff;
      border-radius: 20px;
      padding: 2rem;
      box-shadow: 0 0 15px rgba(0,0,0,0.1);
    }
    .icon-box {
      display: flex;
      justify-content: space-around;
      flex-wrap: wrap;
      gap: 1rem;
      margin-bottom: 2rem;
    }
    .icon-item {
      width: 100px;
      height: 100px;
      border-radius: 15px;
      background: #c8e6c9;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 2rem;
      box-shadow: 2px 2px 10px rgba(0,0,0,0.1);
    }
    label, select, input {
      display: block;
      width: 100%;
      margin: 0.5rem 0;
      padding: 0.8rem;
      border-radius: 10px;
      border: 1px solid #ccc;
    }
    button {
      background-color: #26a69a;
      color: #fff;
      padding: 1rem;
      width: 100%;
      border: none;
      font-size: 1rem;
      border-radius: 10px;
      margin-top: 1rem;
      cursor: pointer;
    }
    .result {
      margin-top: 1.5rem;
      background-color: #b2dfdb;
      padding: 1rem;
      border-radius: 10px;
      font-size: 1.2rem;
      text-align: center;
    }
  </style>
</head>
<body>
  <header>
    <h1>EcoDrop – Water Usage</h1>
  </header>

  <main>
    <div class="icon-box">
      <div class="icon-item" title="Banho 🚿">🛁</div>
      <div class="icon-item" title="Descarga 🚽">🚽</div>
      <div class="icon-item" title="Louça 🍽️">🍽️</div>
      <div class="icon-item" title="Torneira 💧">🚰</div>
    </div>

    <label>Banhos por dia</label>
    <input type="number" id="baths" placeholder="Ex: 2">

    <label>Duração do banho (min)</label>
    <input type="number" id="showerTime" placeholder="Ex: 10">

    <label>Descargas por dia</label>
    <input type="number" id="flushes" placeholder="Ex: 5">

    <label>Lavagens de louça por semana</label>
    <input type="number" id="dishwashing" placeholder="Ex: 7">

    <label>Tempo de uso da torneira (min/dia)</label>
    <input type="number" id="faucetTime" placeholder="Ex: 15">

    <label>Escolha o período</label>
    <select id="period">
      <option value="day">Por Dia</option>
      <option value="month" selected>Por Mês</option>
      <option value="year">Por Ano</option>
    </select>

    <button onclick="calculateWater()">Ver Consumo</button>

    <div class="result" id="resultBox"></div>
  </main>

  <script>
    function calculateWater() {
      const baths = +document.getElementById("baths").value || 0;
      const showerTime = +document.getElementById("showerTime").value || 0;
      const flushes = +document.getElementById("flushes").value || 0;
      const dishwashing = +document.getElementById("dishwashing").value || 0;
      const faucetTime = +document.getElementById("faucetTime").value || 0;
      const period = document.getElementById("period").value;

      const showerL = baths * showerTime * 9;
      const flushL = flushes * 6;
      const dishL = (dishwashing / 7) * 15; // convertido pra diário
      const faucetL = faucetTime * 6;

      const dailyTotal = showerL + flushL + dishL + faucetL;

      let multiplier = 1;
      let label = "dia";

      if (period === "month") {
        multiplier = 30;
        label = "mês";
      } else if (period === "year") {
        multiplier = 365;
        label = "ano";
      }

      const final = Math.round(dailyTotal * multiplier);

      document.getElementById("resultBox").innerHTML = 
        `Você consome cerca de <strong>${final} litros</strong> de água por ${label}.`;
    }
  </script>
</body>
</html><!DOCTYPE html>
<html lang="pt">
<head>
  <meta charset="UTF-8">
  <title>EcoDrop – Water Usage</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #e0f7fa;
      color: #1b5e20;
      margin: 0;
      padding: 0;
    }
    header {
      background: linear-gradient(to right, #81d4fa, #a5d6a7);
      padding: 1rem;
      text-align: center;
    }
    h1 {
      margin: 0;
      font-size: 1.8rem;
    }
    main {
      max-width: 700px;
      margin: 2rem auto;
      background: #ffffff;
      border-radius: 20px;
      padding: 2rem;
      box-shadow: 0 0 15px rgba(0,0,0,0.1);
    }
    .icon-box {
      display: flex;
      justify-content: space-around;
      flex-wrap: wrap;
      gap: 1rem;
      margin-bottom: 2rem;
    }
    .icon-item {
      width: 100px;
      height: 100px;
      border-radius: 15px;
      background: #c8e6c9;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 2rem;
      box-shadow: 2px 2px 10px rgba(0,0,0,0.1);
    }
    label, select, input {
      display: block;
      width: 100%;
      margin: 0.5rem 0;
      padding: 0.8rem;
      border-radius: 10px;
      border: 1px solid #ccc;
    }
    button {
      background-color: #26a69a;
      color: #fff;
      padding: 1rem;
      width: 100%;
      border: none;
      font-size: 1rem;
      border-radius: 10px;
      margin-top: 1rem;
      cursor: pointer;
    }
    .result {
      margin-top: 1.5rem;
      background-color: #b2dfdb;
      padding: 1rem;
      border-radius: 10px;
      font-size: 1.2rem;
      text-align: center;
    }
  </style>
</head>
<body>
  <header>
    <h1>EcoDrop – Water Usage</h1>
  </header>

  <main>
    <div class="icon-box">
      <div class="icon-item" title="Banho 🚿">🛁</div>
      <div class="icon-item" title="Descarga 🚽">🚽</div>
      <div class="icon-item" title="Louça 🍽️">🍽️</div>
      <div class="icon-item" title="Torneira 💧">🚰</div>
    </div>

    <label>Banhos por dia</label>
    <input type="number" id="baths" placeholder="Ex: 2">

    <label>Duração do banho (min)</label>
    <input type="number" id="showerTime" placeholder="Ex: 10">

    <label>Descargas por dia</label>
    <input type="number" id="flushes" placeholder="Ex: 5">

    <label>Lavagens de louça por semana</label>
    <input type="number" id="dishwashing" placeholder="Ex: 7">

    <label>Tempo de uso da torneira (min/dia)</label>
    <input type="number" id="faucetTime" placeholder="Ex: 15">

    <label>Escolha o período</label>
    <select id="period">
      <option value="day">Por Dia</option>
      <option value="month" selected>Por Mês</option>
      <option value="year">Por Ano</option>
    </select>

    <button onclick="calculateWater()">Ver Consumo</button>

    <div class="result" id="resultBox"></div>
  </main>

  <script>
    function calculateWater() {
      const baths = +document.getElementById("baths").value || 0;
      const showerTime = +document.getElementById("showerTime").value || 0;
      const flushes = +document.getElementById("flushes").value || 0;
      const dishwashing = +document.getElementById("dishwashing").value || 0;
      const faucetTime = +document.getElementById("faucetTime").value || 0;
      const period = document.getElementById("period").value;

      const showerL = baths * showerTime * 9;
      const flushL = flushes * 6;
      const dishL = (dishwashing / 7) * 15; // convertido pra diário
      const faucetL = faucetTime * 6;

      const dailyTotal = showerL + flushL + dishL + faucetL;

      let multiplier = 1;
      let label = "dia";

      if (period === "month") {
        multiplier = 30;
        label = "mês";
      } else if (period === "year") {
        multiplier = 365;
        label = "ano";
      }

      const final = Math.round(dailyTotal * multiplier);

      document.getElementById("resultBox").innerHTML = 
        `Você consome cerca de <strong>${final} litros</strong> de água por ${label}.`;
    }
  </script>
</body>
</html><!DOCTYPE html>
<html lang="pt">
<head>
  <meta charset="UTF-8">
  <title>EcoDrop – Water Usage</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #e0f7fa;
      color: #1b5e20;
      margin: 0;
      padding: 0;
    }
    header {
      background: linear-gradient(to right, #81d4fa, #a5d6a7);
      padding: 1rem;
      text-align: center;
    }
    h1 {
      margin: 0;
      font-size: 1.8rem;
    }
    main {
      max-width: 700px;
      margin: 2rem auto;
      background: #ffffff;
      border-radius: 20px;
      padding: 2rem;
      box-shadow: 0 0 15px rgba(0,0,0,0.1);
    }
    .icon-box {
      display: flex;
      justify-content: space-around;
      flex-wrap: wrap;
      gap: 1rem;
      margin-bottom: 2rem;
    }
    .icon-item {
      width: 100px;
      height: 100px;
      border-radius: 15px;
      background: #c8e6c9;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 2rem;
      box-shadow: 2px 2px 10px rgba(0,0,0,0.1);
    }
    label, select, input {
      display: block;
      width: 100%;
      margin: 0.5rem 0;
      padding: 0.8rem;
      border-radius: 10px;
      border: 1px solid #ccc;
    }
    button {
      background-color: #26a69a;
      color: #fff;
      padding: 1rem;
      width: 100%;
      border: none;
      font-size: 1rem;
      border-radius: 10px;
      margin-top: 1rem;
      cursor: pointer;
    }
    .result {
      margin-top: 1.5rem;
      background-color: #b2dfdb;
      padding: 1rem;
      border-radius: 10px;
      font-size: 1.2rem;
      text-align: center;
    }
  </style>
</head>
<body>
  <header>
    <h1>EcoDrop – Water Usage</h1>
  </header>

  <main>
    <div class="icon-box">
      <div class="icon-item" title="Banho 🚿">🛁</div>
      <div class="icon-item" title="Descarga 🚽">🚽</div>
      <div class="icon-item" title="Louça 🍽️">🍽️</div>
      <div class="icon-item" title="Torneira 💧">🚰</div>
    </div>

    <label>Banhos por dia</label>
    <input type="number" id="baths" placeholder="Ex: 2">

    <label>Duração do banho (min)</label>
    <input type="number" id="showerTime" placeholder="Ex: 10">

    <label>Descargas por dia</label>
    <input type="number" id="flushes" placeholder="Ex: 5">

    <label>Lavagens de louça por semana</label>
    <input type="number" id="dishwashing" placeholder="Ex: 7">

    <label>Tempo de uso da torneira (min/dia)</label>
    <input type="number" id="faucetTime" placeholder="Ex: 15">

    <label>Escolha o período</label>
    <select id="period">
      <option value="day">Por Dia</option>
      <option value="month" selected>Por Mês</option>
      <option value="year">Por Ano</option>
    </select>

    <button onclick="calculateWater()">Ver Consumo</button>

    <div class="result" id="resultBox"></div>
  </main>

  <script>
    function calculateWater() {
      const baths = +document.getElementById("baths").value || 0;
      const showerTime = +document.getElementById("showerTime").value || 0;
      const flushes = +document.getElementById("flushes").value || 0;
      const dishwashing = +document.getElementById("dishwashing").value || 0;
      const faucetTime = +document.getElementById("faucetTime").value || 0;
      const period = document.getElementById("period").value;

      const showerL = baths * showerTime * 9;
      const flushL = flushes * 6;
      const dishL = (dishwashing / 7) * 15; // convertido pra diário
      const faucetL = faucetTime * 6;

      const dailyTotal = showerL + flushL + dishL + faucetL;

      let multiplier = 1;
      let label = "dia";

      if (period === "month") {
        multiplier = 30;
        label = "mês";
      } else if (period === "year") {
        multiplier = 365;
        label = "ano";
      }

      const final = Math.round(dailyTotal * multiplier);

      document.getElementById("resultBox").innerHTML = 
        `Você consome cerca de <strong>${final} litros</strong> de água por ${label}.`;
    }
  </script>
</body>
</html>h
