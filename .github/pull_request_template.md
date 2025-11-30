<!DOCTYPE html>
<html>
<head>
<title>Cleanup — Early Access</title>
<style>
body {
  font-family: Arial, sans-serif;
  background: #101820;
  color: white;
  text-align: center;
  margin: 0;
}

header {
  background: #1c2b3a;
  padding: 20px;
  font-size: 30px;
  font-weight: bold;
}

button {
  padding: 15px 25px;
  margin: 10px;
  font-size: 20px;
  border: none;
  border-radius: 10px;
  background: #2d89ef;
  color: white;
  cursor: pointer;
}
button:hover {
  background: #1e5fbf;
}

.screen {
  display: none;
  padding: 20px;
}

img.pixel-broom {
  width: 120px;
}

/* BOX FOR UNUSED APPS */
.app-box {
  width: 300px;
  height: 250px;
  margin: auto;
  border: 3px solid white;
  border-radius: 10px;
  padding: 10px;
  background: #182430;
}

.app-item {
  font-size: 22px;
  background: #243447;
  padding: 8px;
  margin: 6px;
  border-radius: 6px;
}

/* POPCORN GAME */
#popcornBucket {
  width: 120px;
  height: 150px;
  background: yellow;
  margin: 20px auto;
  position: relative;
  border-radius: 10px;
}
.pop {
  width: 15px;
  height: 15px;
  background: white;
  position: absolute;
  border-radius: 50%;
}
</style>
</head>
<body>

<header>
  Cleanup — Early Access
</header>

<img class="pixel-broom" src="broom.png">

<h2>Choose a section</h2>

<button onclick="show('unusedScreen')">📦 Unused Apps</button>
<button onclick="show('settingsScreen')">⚙ Settings</button>
<button onclick="show('gamesScreen')">🍿 Mini Games</button>
<button onclick="show('vipScreen')">⭐ VIP Room</button>

<!-- UNUSED APPS -->
<div id="unusedScreen" class="screen">
  <h2>Unused Apps Box</h2>
  <div class="app-box" id="appList"></div>
</div>

<!-- SETTINGS -->
<div id="settingsScreen" class="screen">
  <h2>Settings</h2>
  <p>Select apps to PROTECT:</p>
  <button onclick="protect('Hole.io')">Hole.io</button>
  <button onclick="protect('Grow a Garden')">Grow a Garden</button>
  <button onclick="protect('Max')">Max</button>
  <button onclick="protect('Merge Anything')">Merge Anything</button>
  <p id='protectedList'></p>
</div>

<!-- GAMES -->
<div id="gamesScreen" class="screen">
  <h2>Popcorn Game</h2>
  <p>Tap to fill the bucket!</p>
  <div id="popcornBucket" onclick="popcorn()"></div>
</div>

<!-- VIP ROOM -->
<div id="vipScreen" class="screen">
  <h2>⭐ VIP Room</h2>
  <p>You joined Early Access!</p>
  <p>Achievement unlocked: <b>EARLY CLEANER</b></p>
</div>

<script>
function show(id) {
  document.querySelectorAll(".screen").forEach(s => s.style.display = "none");
  document.getElementById(id).style.display = "block";
}

/* UNUSED APPS LIST */
let unusedApps = ["Hole.io", "Grow a Garden", "Max", "Merge Anything"];
let protectedApps = [];

function loadApps() {
  const appList = document.getElementById("appList");
  appList.innerHTML = "";
  unusedApps.forEach(app => {
    if (!protectedApps.includes(app)) {
      const div = document.createElement("div");
      div.className = "app-item";
      div.innerText = app;
      appList.appendChild(div);
    }
  });
}
loadApps();

/* PROTECT APP */
function protect(app) {
  if (!protectedApps.includes(app)) {
    protectedApps.push(app);
    document.getElementById("protectedList").innerText =
      "Protected: " + protectedApps.join(", ");
  }
  loadApps();
}

/* POPCORN GAME */
function popcorn() {
  const bucket = document.getElementById("popcornBucket");
  const pop = document.createElement("div");
  pop.className = "pop";
  pop.style.left = Math.random() * 100 + "px";
  pop.style.top = Math.random() * 120 + "px";
  bucket.appendChild(pop);
}
</script>

</body>
</html>
