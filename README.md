# energy-bill-optimizer
Energy Bill Optimization Problem in existing electricity tracking apps: They only show usage data. Your Solution: Predict next month’s bill. Suggest which appliances cause high bills. Give cost-saving tips (like “Switch off router at night, saves ₹200/month”). develop this idea

Program:
 index.hmtl
 ```
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Smart Energy Bill Optimizer</title>
<meta name="viewport" content="width=device-width, initial-scale=1">


<script src="https://cdn.tailwindcss.com"></script>


<style>
body {
  min-height: 100vh;
  background: linear-gradient(-45deg,
    #0f766e,
    #22c55e,
    #38bdf8,
    #6366f1
  );
  background-size: 400% 400%;
  animation: gradientMove 15s ease infinite;
  font-family: 'Segoe UI', sans-serif;
}

@keyframes gradientMove {
  0% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
}
</style>
</head>

<body>

<div class="fixed inset-0 -z-10 overflow-hidden">
  <div class="absolute w-72 h-72 bg-green-400 rounded-full blur-3xl opacity-30 top-10 left-10 animate-pulse"></div>
  <div class="absolute w-96 h-96 bg-blue-400 rounded-full blur-3xl opacity-30 bottom-10 right-10 animate-pulse"></div>
</div>


<header class="text-center text-white p-8">
  <h1 class="text-4xl font-bold">⚡ Smart Energy Bill Optimizer</h1>
  <p class="mt-2 text-lg">Predict • Analyze • Save Electricity</p>
</header>


<main class="max-w-4xl mx-auto p-6 space-y-6">


<div class="bg-white/70 backdrop-blur-md p-6 rounded-xl shadow">
  <h2 class="text-xl font-semibold mb-2">👋 How to use this website</h2>
  <ul class="list-disc ml-6 text-gray-700">
    <li>Enter appliance name, power & daily usage</li>
    <li>Add multiple appliances</li>
    <li>View predicted bill and savings tips</li>
  </ul>
</div>


<div class="bg-white/70 backdrop-blur-md p-6 rounded-xl shadow">
  <h2 class="text-xl font-semibold mb-4">🔌 Appliance Details</h2>

  <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
    <input id="name" class="border p-2 rounded" placeholder="Appliance Name (AC)">
    <input id="power" type="number" class="border p-2 rounded" placeholder="Power (Watts)">
    <input id="hours" type="number" class="border p-2 rounded" placeholder="Hours / Day">
  </div>

  <button onclick="addAppliance()"
    class="mt-4 bg-green-600 text-white px-6 py-2 rounded hover:bg-green-700">
    Add Appliance
  </button>
</div>


<div id="results" class="hidden bg-white/70 backdrop-blur-md p-6 rounded-xl shadow">
  <h2 class="text-xl font-semibold mb-3">📊 Analysis Result</h2>
  <div id="output" class="space-y-1"></div>
  <hr class="my-3">
  <div id="prediction" class="font-bold text-lg"></div>
  <div id="tips" class="mt-4 text-green-700"></div>
</div>

</main>


<script>
let totalCost = 0;
let applianceCount = 0;

function addAppliance() {
  const name = document.getElementById("name").value;
  const power = document.getElementById("power").value;
  const hours = document.getElementById("hours").value;

  if (!name || !power || !hours) {
    alert("Please fill all fields");
    return;
  }

  const costPerUnit = 6;
  const units = (power * hours * 30) / 1000;
  const cost = units * costPerUnit;

  totalCost += cost;
  applianceCount++;

  document.getElementById("results").classList.remove("hidden");

  document.getElementById("output").innerHTML +=
    `🔹 <b>${name}</b>: ₹${cost.toFixed(2)} / month<br>`;

  document.getElementById("prediction").innerHTML =
    `🔮 Predicted Next Month Bill: ₹${totalCost.toFixed(2)}`;

  if (cost > 500) {
    document.getElementById("tips").innerHTML +=
      `⚠ Reduce usage of <b>${name}</b> by 1 hour/day → Save approx ₹${(cost/6).toFixed(0)}<br>`;
  }

  document.getElementById("name").value = "";
  document.getElementById("power").value = "";
  document.getElementById("hours").value = "";
}
</script>

</body>
</html>
```

