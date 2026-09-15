# <!DOCTYPE html>  <html lang="en">  
<head>  
  <meta charset="UTF-8">  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  
  <title>Solar PV Engineer Pro</title>  
  <meta name="theme-color" content="#0f172a">  
  <style>  
    :root {  
      --bg: #0f172a;  
      --card-bg: #1e293b;  
      --accent: #f59e0b;  
      --accent-hover: #d97706;  
      --text: #f8fafc;  
      --text-muted: #94a3b8;  
      --border: #334155;  
      --success: #10b981;  
      --error: #ef4444;  
      --info: #3b82f6;  
    }  
    * { box-sizing: border-box; margin: 0; padding: 0; font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif; }  
    body { background-color: var(--bg); color: var(--text); padding-bottom: 70px; }  
    header {  
      background-color: #020617;  
      padding: 16px;  
      text-align: center;  
      border-bottom: 2px solid var(--accent);  
      position: sticky;  
      top: 0;  
      z-index: 100;  
    }  
    header h1 { font-size: 1.2rem; color: var(--accent); letter-spacing: 1px; }  
    header p { font-size: 0.75rem; color: var(--text-muted); }  
    nav {  
      position: fixed;  
      bottom: 0; left: 0; right: 0;  
      background-color: #020617;  
      display: flex;  
      justify-content: space-around;  
      padding: 10px 0;  
      border-top: 1px solid var(--border);  
      z-index: 100;  
    }  
    nav button {  
      background: none; border: none; color: var(--text-muted);  
      font-size: 0.75rem; font-weight: 600; cursor: pointer;  
      display: flex; flex-direction: column; align-items: center; gap: 4px;  
    }  
    nav button.active { color: var(--accent); }  
    .container { padding: 16px; max-width: 800px; margin: 0 auto; }  
    .tab-content { display: none; }  
    .tab-content.active { display: block; }  
    .card {  
      background-color: var(--card-bg);  
      border: 1px solid var(--border);  
      border-radius: 8px;  
      padding: 16px;  
      margin-bottom: 16px;  
    }  
    .card h2 { font-size: 1.1rem; color: var(--accent); margin-bottom: 12px; }  
    .card h3 { font-size: 0.95rem; color: #38bdf8; margin: 12px 0 6px 0; }  
      
    label { display: block; font-size: 0.85rem; margin-top: 10px; color: var(--text-muted); }  
    input, select {  
      width: 100%; padding: 10px; margin-top: 4px;  
      background: #090d16; border: 1px solid var(--border);  
      border-radius: 6px; color: #fff; font-size: 0.9rem;  
    }  
    button.btn-action {  
      width: 100%; padding: 12px; margin-top: 16px;  
      background-color: var(--accent); color: #000;  
      font-weight: bold; font-size: 1rem; border: none;  
      border-radius: 6px; cursor: pointer;  
    }  
    button.btn-action:hover { background-color: var(--accent-hover); }  
    .result-box {  
      margin-top: 16px; padding: 12px; background: #090d16;  
      border-radius: 6px; border-left: 4px solid var(--accent);  
      font-size: 0.85rem; line-height: 1.5;  
    }  
    .status-pass { color: var(--success); font-weight: bold; }  
    .status-fail { color: var(--error); font-weight: bold; }  
    .badge { display: inline-block; padding: 2px 6px; border-radius: 4px; font-size: 0.7rem; font-weight: bold; }  
    .badge-pv { background: #3b82f6; color: #fff; }  
    .spec-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; font-size: 0.8rem; }  
    .spec-item { background: #090d16; padding: 8px; border-radius: 4px; }  
    .spec-item span { color: var(--text-muted); display: block; font-size: 0.7rem; }  
  </style>  
</head>  
<body>  
<header>  
  <h1>SOLAR PV ENGINEER PRO</h1>  
  <p>Professional Solar Engineering &amp; Sizing Suite</p>  
</header>  
<div class="container">  
  <!-- TAB 1: DESIGN CHALLENGE -->  
  <div id="challenge" class="tab-content active">  
    <div class="card">  
      <h2>⚡ Engineer Test: 10 kW System Challenge</h2>  
      <p style="font-size:0.85rem; color:var(--text-muted);">  
        <strong>Scenario:</strong> You are designing a commercial 10 kW Grid-Tied PV system. Select the appropriate string topology, cable sizes, and protective devices, then click <em>"Check My Design"</em>.  
      </p>  
        
      <div style="margin-top:12px;" class="card">  
        <h3>📋 System Specifications</h3>  
        <div class="spec-grid">  
          <div class="spec-item"><span>Inverter AC Rating</span>10 kW (3-Phase)</div>  
          <div class="spec-item"><span>Max DC Input Voltage</span>1000 V</div>  
          <div class="spec-item"><span>MPPT Voltage Range</span>200 V - 850 V</div>  
          <div class="spec-item"><span>MPPT Tracker Count</span>2 Trackers</div>  
          <div class="spec-item"><span>PV Module STC Power</span>550 Wp</div>  
          <div class="spec-item"><span>Module Vmp / Imp</span>41.5 V / 13.25 A</div>  
          <div class="spec-item"><span>Module Voc / Isc</span>49.5 V / 14.00 A</div>  
          <div class="spec-item"><span>Temp Coeff (Voc)</span>-0.27 % / °C</div>  
        </div>  
      </div>  
      <label for="c_panels">1. Total Panel Quantity</label>  
      <input type="number" id="c_panels" value="18" placeholder="e.g. 18">  
      <label for="c_strings">2. String Configuration</label>  
      <select id="c_strings">  
        <option value="1x18">1 String of 18 Panels</option>  
        <option value="2x9" selected>2 Strings of 9 Panels</option>  
        <option value="2x10">2 Strings of 10 Panels</option>  
      </select>  
      <label for="c_mppt">3. MPPT Allocation</label>  
      <select id="c_mppt">  
        <option value="1_per_mppt" selected>1 String into MPPT 1, 1 String into MPPT 2</option>  
        <option value="parallel_mppt1">2 Strings in Parallel into MPPT 1</option>  
      </select>  
      <label for="c_dc_cable">4. DC Cable Cross-Section Area (One-way 35m)</label>  
      <select id="c_dc_cable">  
        <option value="2.5">2.5 mm²</option>  
        <option value="4" selected>4.0 mm²</option>  
        <option value="6">6.0 mm²</option>  
        <option value="10">10.0 mm²</option>  
      </select>  
      <label for="c_protection">5. String Fuse / Overcurrent Protection Rating</label>  
      <select id="c_protection">  
        <option value="15">15 A</option>  
        <option value="20" selected>20 A</option>  
        <option value="25">25 A</option>  
        <option value="32">32 A</option>  
      </select>  
      <button class="btn-action" onclick="checkDesign()">Check My Design</button>  
      <div id="challenge-results" class="result-box" style="display:none;"></div>  
    </div>  
  </div>  
  <!-- TAB 2: CALCULATORS -->  
  <div id="tools" class="tab-content">  
    <div class="card">  
      <h2>📐 Dynamic PV &amp; Cable Sizing Tool</h2>  
        
      <h3>Module &amp; Temperature Dynamics</h3>  
      <label for="calc_temp">Minimum Cold Temperature (°C)</label>  
      <input type="number" id="calc_temp" value="-10">  
      <label for="calc_panels_per_string">Panels per String</label>  
      <input type="number" id="calc_panels_per_string" value="10">  
      <button class="btn-action" onclick="runCalculations()">Run System Calculations</button>  
      <div id="calc-results" class="result-box" style="display:none;"></div>  
    </div>  
  </div>  
  <!-- TAB 3: LEARNING HUB -->  
  <div id="learn" class="tab-content">  
    <div class="card">  
      <h2>📚 Solar Engineering Reference Hub</h2>  
        
      <h3>1. Temperature Coefficient &amp; Cold Weather Voc</h3>  
      <p style="font-size:0.85rem; color:var(--text-muted); line-height:1.4;">  
        PV modules increase open-circuit voltage ($V_{oc}$) in cold conditions. String design must calculate max voltage at local minimum temperatures to prevent exceeding inverter input ratings.  
        <br><strong>Formula:</strong> $V_{oc(max)} = V_{oc(STC)} \times [1 + (\gamma_{Voc} / 100) \times (T_{min} - 25)]$.  
      </p>  
      <h3>2. Protection Device Sizing Rules</h3>  
      <p style="font-size:0.85rem; color:var(--text-muted); line-height:1.4;">  
        Under standard safety codes (e.g., NEC 690.8 / IEC 60364-7-712), overcurrent protection rating is sized using standard continuous safety factors:  
        <br><strong>Continuous Current:</strong> $I_{design} = I_{sc} \times 1.25$.  
        <br><strong>OCPD Rating:</strong> $I_{OCPD} = I_{sc} \times 1.25 \times 1.25 = I_{sc} \times 1.56$.  
      </p>  
      <h3>3. Cable Sizing &amp; Voltage Drop Rules</h3>  
      <p style="font-size:0.85rem; color:var(--text-muted); line-height:1.4;">  
        Target DC side voltage drop should remain under <strong>2.0%</strong> to prevent yield loss.  
        <br><strong>Voltage Drop:</strong> $\Delta V = \frac{2 \times L \times I \times \rho}{A}$  
        <br>Where $L$ = length (m), $I$ = current (A), $\rho$ = copper resistivity, $A$ = cross-sectional area ($\text{mm}^2$).  
      </p>  
      <h3>4. Multi-MW Design Hierarchy</h3>  
      <div style="font-size:0.85rem; color:var(--text-muted); margin-top:6px;">  
        • <strong>5 kW - 10 kW:</strong> Single-phase / 3-phase residential string inverters.<br>  
        • <strong>50 kW - 100 kW:</strong> Commercial string inverters with multiple MPPT trackers.<br>  
        • <strong>1 MW+:</strong> Utility-scale central inverters or high-voltage decentralized string inverters (1500 V DC systems).  
      </div>  
    </div>  
  </div>  
</div>  
<!-- NAVIGATION -->  
<nav>  
  <button class="active" onclick="switchTab('challenge', this)">  
    <span>⚡</span>Test Mode  
  </button>  
  <button onclick="switchTab('tools', this)">  
    <span>📐</span>Calculators  
  </button>  
  <button onclick="switchTab('learn', this)">  
    <span>📚</span>Academy  
  </button>  
</nav>  
<script>  
  function switchTab(tabId, el) {  
    document.querySelectorAll('.tab-content').forEach(t => t.classList.remove('active'));  
    document.querySelectorAll('nav button').forEach(b => b.classList.remove('active'));  
    document.getElementById(tabId).classList.add('active');  
    el.classList.add('active');  
  }  
  function checkDesign() {  
    const panels = parseInt(document.getElementById('c_panels').value);  
    const strings = document.getElementById('c_strings').value;  
    const mppt = document.getElementById('c_mppt').value;  
    const cable = parseFloat(document.getElementById('c_dc_cable').value);  
    const protection = parseInt(document.getElementById('c_protection').value);  
    let logs = [];  
    let passed = true;  
    // 1. Array Sizing Check  
    const totalPower = panels * 550;  
    if (panels === 18 || panels === 19 || panels === 20) {  
      logs.push(`✅ <span class="status-pass">Array Capacity:</span> ${totalPower} Wp (${(totalPower/1000).toFixed(2)} kW DC). Excellent DC/AC ratio for 10 kW AC inverter.`);  
    } else {  
      passed = false;  
      logs.push(`❌ <span class="status-fail">Array Capacity:</span> ${totalPower} Wp is inappropriate for a 10 kW inverter.`);  
    }  
    // 2. Voltage & Temperature Sizing (Tmin = -10°C)  
    // Voc(STC) = 49.5, Coeff = -0.27%/°C. Delta T = -10 - 25 = -35°C  
    // Voc_max = 49.5 * (1 + (-0.0027 * -35)) = 49.5 * 1.0945 = 54.18 V  
    const Voc_STC = 49.5;  
    const Voc_max = Voc_STC * (1 + (-0.0027 * -35));  
      
    let panelsPerString = 0;  
    if (strings === '1x18') panelsPerString = 18;  
    if (strings === '2x9') panelsPerString = 9;  
    if (strings === '2x10') panelsPerString = 10;  
    const stringVocMax = panelsPerString * Voc_max;  
    const stringVmpSTC = panelsPerString * 41.5;  
    if (strings === '1x18') {  
      passed = false;  
      logs.push(`❌ <span class="status-fail">Topology Error:</span> 1 string of 18 panels yields max $V_{oc}$ of ${stringVocMax.toFixed(1)} V at -10°C. Exceeds MPPT upper tracking window (850V).`);  
    } else {  
      logs.push(`✅ <span class="status-pass">String Voltage:</span> ${panelsPerString} panels per string yields ${stringVocMax.toFixed(1)} V max cold $V_{oc}$ (safe under 1000V limit) and ${stringVmpSTC.toFixed(1)} V nominal $V_{mp}$ (well inside 200V-850V MPPT range).`);  
    }  
    // 3. MPPT Allocation  
    if (mppt === '1_per_mppt') {  
      logs.push(`✅ <span class="status-pass">MPPT Allocation:</span> Allocating 1 string per MPPT tracker optimizes yield and eliminates mismatch losses.`);  
    } else {  
      logs.push(`ℹ️ <span class="status-pass">MPPT Allocation:</span> Paralleling onto 1 MPPT is acceptable if currents match, but separate MPPT allocation provides better yield.`);  
    }  
    // 4. DC Cable Voltage Drop Check (35m one way, Imp = 13.25A, Copper rho = 0.0175)  
    // dV = (2 * 35 * 13.25 * 0.0175) / Area  
    const dV = (2 * 35 * 13.25 * 0.0175) / cable;  
    const dV_percent = (dV / stringVmpSTC) * 100;  
    if (dV_percent <= 2.0) {  
      logs.push(`✅ <span class="status-pass">DC Cable Sizing:</span> ${cable} mm² cable yields a voltage drop of ${dV.toFixed(2)} V (${dV_percent.toFixed(2)}%), which is below the recommended 2.0% limit.`);  
    } else {  
      passed = false;  
      logs.push(`❌ <span class="status-fail">Cable Drop Error:</span> ${cable} mm² cable results in ${dV_percent.toFixed(2)}% voltage drop (${dV.toFixed(2)} V). Upgrade to at least 4.0 mm² or 6.0 mm².`);  
    }  
    // 5. Protection Sizing Check (Isc = 14.0A, Rule: Isc * 1.56 = 21.84A)  
    if (protection >= 20 && protection <= 25) {  
      logs.push(`✅ <span class="status-pass">OCPD Protection:</span> ${protection} A fuse/breaker selected. Matches standard requirements ($I_{sc} \\times 1.25 \\times 1.25 = 21.84$ A).`);  
    } else {  
      passed = false;  
      logs.push(`❌ <span class="status-fail">Protection Rating Error:</span> ${protection} A is incorrect. $I_{sc} \\times 1.25 \\times 1.25 = 21.84$ A. Select a 20 A or 25 A protective device.`);  
    }  
    // Display Results  
    const resBox = document.getElementById('challenge-results');  
    resBox.style.display = 'block';  
    resBox.innerHTML = `  
      <h3 style="color:${passed ? 'var(--success)' : 'var(--error)'}; margin-bottom:8px;">  
        ${passed ? '🎉 DESIGN APPROVED!' : '⚠️ REVISION REQUIRED'}  
      </h3>  
      ${logs.map(l => `<p style="margin-bottom:6px;">${l}</p>`).join('')}  
    `;  
  }  
  function runCalculations() {  
    const temp = parseFloat(document.getElementById('calc_temp').value);  
    const panels = parseInt(document.getElementById('calc_panels_per_string').value);  
    // Datasheet STC values  
    const Voc_STC = 49.5;  
    const Vmp_STC = 41.5;  
    const coeff = -0.27; // %/C  
    const deltaT = temp - 25;  
    const Voc_temp = Voc_STC * (1 + (coeff/100 * deltaT));  
    const stringVoc = Voc_temp * panels;  
    const stringVmp = Vmp_STC * panels;  
    const resBox = document.getElementById('calc-results');  
    resBox.style.display = 'block';  
    resBox.innerHTML = `  
      <h3>Calculation Summary (${panels} panels @ ${temp}°C)</h3>  
      <p>• Single Panel $V_{oc}$ at ${temp}°C: <strong>${Voc_temp.toFixed(2)} V</strong></p>  
      <p>• Max String $V_{oc}$ (${temp}°C): <strong>${stringVoc.toFixed(2)} V</strong></p>  
      <p>• Nominal String $V_{mp}$ (25°C): <strong>${stringVmp.toFixed(2)} V</strong></p>  
      <p>• Operating Status: <strong>${stringVoc > 1000 ? '<span class="status-fail">OVERVOLTAGE WARNING (>1000V)</span>' : '<span class="status-pass">SAFE VOLTAGE RANGE</span>'}</strong></p>  
    `;  
  }  
</script>  
</body>  
</html>  Please make me a apps which one I can install my phone for use