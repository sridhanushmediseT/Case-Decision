<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Case Decision Assistant</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">

  <style>
    /* basic theme */
    :root {
      --primary: #2255aa;
      --primary-dark: #163a77;
      --bg: #f4f5f7;
      --border: #d1d5db;
      --text-main: #111827;
      --text-muted: #6b7280;
    }

    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Arial, sans-serif;
      background: var(--bg);
      color: var(--text-main);
    }

    header {
      background: var(--primary);
      color: #fff;
      padding: 12px 20px;
      display: flex;
      align-items: center;
      box-shadow: 0 2px 4px rgba(0,0,0,0.08);
    }

    .brand-title {
      font-weight: 600;
      font-size: 16px;
    }

    .brand-subtitle {
      font-size: 12px;
      opacity: 0.85;
    }

    main {
      max-width: 840px;
      margin: 24px auto;
      padding: 0 12px 32px;
    }

    .card {
      background: #fff;
      border-radius: 8px;
      border: 1px solid var(--border);
      padding: 18px 18px 22px;
      box-shadow: 0 4px 12px rgba(15,23,42,0.08);
    }

    h1 {
      font-size: 20px;
      margin: 0 0 4px;
    }

    .subtitle {
      font-size: 13px;
      color: var(--text-muted);
      margin-bottom: 14px;
    }

    .meta-row {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      font-size: 11px;
      color: var(--text-muted);
      margin-bottom: 16px;
    }

    .meta-pill1 {
      padding: 3px 8px;
      border-radius: 999px;
      border: 1px solid #ff0f0f;
      background: #f9fafb;
    }

    .meta-pill {
      padding: 3px 8px;
      border-radius: 999px;
      border: 1px solid #e5e7eb;
      background: #f9fafb;
    }

    .step {
      margin-bottom: 14px;
      padding: 12px 12px 14px;
      border-radius: 6px;
      border: 1px solid #e5e7eb;
      background: #fafafa;
    }

    .step-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 8px;
    }

    .step-title {
      font-size: 13px;
      font-weight: 600;
    }

    .step-badge {
      font-size: 11px;
      padding: 1px 7px;
      border-radius: 999px;
      background: #e5edf9;
      color: var(--primary-dark);
    }

    label {
      display: block;
      margin: 4px 0 3px;
      font-size: 13px;
    }

    input,
    select,
    textarea {
      width: 100%;
      max-width: 420px;
      padding: 6px 8px;
      font-size: 13px;
      border-radius: 4px;
      border: 1px solid #d1d5db;
      font-family: inherit;
    }

    input:focus,
    select:focus,
    textarea:focus {
      outline: none;
      border-color: var(--primary);
      box-shadow: 0 0 0 1px rgba(34,85,170,0.25);
    }

    .btn {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      padding: 6px 12px;
      border-radius: 999px;
      font-size: 13px;
      border: none;
      cursor: pointer;
      margin-top: 8px;
    }

    .btn-primary {
      background: var(--primary);
      color: #fff;
    }

    .btn-primary:hover {
      background: var(--primary-dark);
    }

    .info {
      font-size: 11px;
      color: var(--text-muted);
      margin-top: 4px;
    }

    .note {
      font-size: 11px;
      color: var(--primary-dark);
      margin-top: 6px;
      padding: 6px 8px;
      border-radius: 4px;
      background: #eef3ff;
      border: 1px solid #c6d4ff;
    }

    .hidden {
      display: none;
    }

    .result {
      margin-top: 14px;
      padding: 10px 12px;
      border-radius: 6px;
      font-size: 13px;
      display: flex;
      gap: 8px;
      align-items: center;
    }

    .ok {
      background: #ecfdf3;
      border: 1px solid #bbf7d0;
      color: #166534;
    }

    .nok {
      background: #fef2f2;
      border: 1px solid #fecaca;
      color: #b91c1c;
    }

    .result-label {
      font-weight: 600;
      text-transform: uppercase;
      font-size: 10px;
      letter-spacing: 0.06em;
    }

    .result-text {
      flex: 1;
    }

    .footer-note {
      margin-top: 12px;
      font-size: 10px;
      color: var(--text-muted);
      text-align: right;
    }

    @media (max-width: 600px) {
      header {
        padding: 10px 14px;
      }
      .card {
        padding: 14px 12px 18px;
      }
    }
  </style>
</head>
<body>
<header>
  <div>
    <div class="brand-title">Case Decision Practice Portal</div>
    <div class="brand-subtitle">Decision Assistant · Internal use</div>
  </div>
</header>

<main>
  <div class="card">
    <h1>Case Decision Assistant</h1>
    <div class="subtitle">
      Simple helper to decide if we work on a case, who should own it, and what to do next.
    </div>

    <div class="meta-row">
      <div class="meta-pill">Case Intake &amp;</div>
      <div class="meta-pill">Timezone: IST (Asia/Kolkata)</div>
      <div class="meta-pill1">PROTOTYPE</div>
    </div>

    <!-- Step 1: Case ID (mandatory) -->
    <div class="step" id="step1">
      <div class="step-header">
        <div class="step-title">Step 1 · Case details</div>
        <span class="step-badge">Required</span>
      </div>
      <label for="caseId">Case ID <span style="color:#b91c1c">*</span></label>
      <input
        type="text"
        id="caseId"
        placeholder="Enter the Case ID"
        oninput="clearResult(); updateSummary();"
      >
      <div class="info">Case ID must be filled before moving ahead.</div>
    </div>

    <!-- Step 2: Serial Number -->
    <div class="step" id="step2">
      <div class="step-header">
        <div class="step-title">Step 2 · Serial number</div>
      </div>
      <label for="serialNumber">Serial number</label>
      <input
        type="text"
        id="serialNumber"
        placeholder="Enter the Serial number"
        oninput="updateSummary();"
      >
      <div class="info">
        Allowed prefixes: NLHA0, NLHB0, USHA0, USHB0, FRHA0, FRHB0, JPHA0, JPHB0
      </div>
      <button type="button" class="btn btn-primary" onclick="checkSerial()">Validate serial</button>
    </div>

    <!-- Step 3: Country -->
    <div class="step hidden" id="step3">
      <div class="step-header">
        <div class="step-title">Step 3 · Country &amp; coverage</div>
      </div>
      <label for="country">Country</label>
      <select id="country" onchange="checkCountry(); updateSummary();">
        <option value="">Select a country…</option>
        <option value="US">United States (US)</option>
        <option value="BE">Belgium (BE)</option>
        <option value="NL">Netherlands (NL)</option>
        <option value="LU">Luxembourg (LU)</option>
        <option value="DK">Denmark (DK)</option>
        <option value="NO">Norway (NO)</option>
        <option value="SE">Sweden (SE)</option>
        <option value="FI">Finland (FI)</option>
        <option value="EE">Estonia (EE)</option>
        <option value="LV">Latvia (LV)</option>
        <option value="IS">Iceland (IS)</option>
        <option value="SJ">Svalbard and Jan Mayen (SJ)</option>
        <option value="FO">Faroe Islands (FO)</option>
        <option value="OTHERS">Other country</option>
      </select>
      <div class="note hidden" id="countryNote"></div>
    </div>

    <!-- Step 4: Account type -->
    <div class="step hidden" id="step4">
      <div class="step-header">
        <div class="step-title">Step 4 · Account type</div>
      </div>
      <label for="isPublicAccount">Is this a Public Account?</label>
      <select id="isPublicAccount" onchange="checkAccount(); updateSummary();">
        <option value="">Select…</option>
        <option value="yes">Yes – Public Account</option>
        <option value="no">No – Not a Public Account</option>
      </select>
    </div>

    <!-- Step 5: Case origin -->
    <div class="step hidden" id="step5">
      <div class="step-header">
        <div class="step-title">Step 5 · Case origin</div>
      </div>
      <label for="origin">Case origin</label>
      <select id="origin" onchange="checkOrigin(); updateSummary();">
        <option value="">Select…</option>
        <option value="irs">IRS</option>
        <option value="phone">Phone</option>
        <option value="chat">Chat</option>
      </select>
    </div>

    <!-- Step 6: Complexity / SFDC -->
    <div class="step hidden" id="step6">
      <div class="step-header">
        <div class="step-title">Step 6 · Complexity &amp; SFDC search</div>
      </div>
      <label for="complexIssue">
        Is the origin Phone/Chat, or is this a complex issue you do not understand?
      </label>
      <select id="complexIssue" onchange="checkComplex(); updateSummary();">
        <option value="">Select…</option>
        <option value="yes">Yes</option>
        <option value="no">No</option>
      </select>
      <div class="info hidden" id="sfdcHint">
        Tip: Search the issue in SFDC and look at similar cases / articles.
      </div>
    </div>

    <!-- Step 7: POA, email, troubleshooting -->
    <div class="step hidden" id="step7">
      <div class="step-header">
        <div class="step-title">Step 7 · POA &amp; communication</div>
      <!--  <span class="step-badge">Action</span> -->
      </div>
      <div class="info">
        Prepare the POA, send the initial email, and update troubleshooting notes in the case.
      </div>
    </div>

    <!-- Step 8: Delay -->
    <div class="step hidden" id="step8">
      <div class="step-header">
        <div class="step-title">Step 8 · Delay / ETA</div>
      <!--  <span class="step-badge">SLA</span> -->
      </div>
      <div class="info">
        If needed, update delay / ETA on the case and continue work.
      </div>
    </div>

    <!-- Step 9: Summary -->
    <div class="step" id="summaryStep">
      <div class="step-header">
        <div class="step-title">Summary · Entered details</div>
      </div>
      <div class="info">This updates as you move through the steps.</div>
      <textarea
        id="summaryBox"
        rows="6"
        readonly
        style="margin-top:6px; font-size:12px; font-family:monospace;"
      ></textarea>
    </div>

    <!-- Result area -->
    <div id="result" class="result hidden">
      <div class="result-label" id="resultLabel"></div>
      <div class="result-text" id="resultText"></div>
    </div>

    <div class="footer-note">
      Internal helper only. Always follow local procedures and escalation rules.
    </div>
  </div>
</main>

<script>
  // Prefixes we accept for serial
  const allowedPrefixes = [
    "NLHA0", "NLHB0",
    "USHA0", "USHB0",
    "FRHA0", "FRHB0",
    "JPHA0", "JPHB0"
  ];

  // Countries where OBH rules apply
  const obhCountries = [
    "BE","NL","LU","DK","NO","SE","FI","EE","LV","IS","SJ","FO"
  ];

  // current time in IST as "HH:MM"
  function getCurrentISTTime() {
    const now = new Date();
    const istString = now.toLocaleString("en-US", { timeZone: "Asia/Kolkata" });
    const istDate = new Date(istString);
    const h = String(istDate.getHours()).padStart(2, "0");
    const m = String(istDate.getMinutes()).padStart(2, "0");
    return h + ":" + m;
  }

  function isAfter(time, compareTo) {
    return time > compareTo;
  }

  function isBefore(time, compareTo) {
    return time < compareTo;
  }

  function showStep(id) {
    const el = document.getElementById(id);
    if (el) el.classList.remove("hidden");
  }

  function hideStepsFrom(ids) {
    ids.forEach(function (id) {
      const el = document.getElementById(id);
      if (el) el.classList.add("hidden");
    });
  }

  function clearResult() {
    const result = document.getElementById("result");
    result.className = "result hidden";
    document.getElementById("resultLabel").textContent = "";
    document.getElementById("resultText").textContent = "";
  }

  function showResult(text, canWork) {
    const result = document.getElementById("result");
    const label = document.getElementById("resultLabel");
    const body = document.getElementById("resultText");

    label.textContent = canWork ? "In scope" : "Out of scope";
    body.textContent = text;

    result.classList.remove("hidden", "ok", "nok");
    result.classList.add(canWork ? "ok" : "nok");
  }

  // Step 2: Serial, but also enforce Case ID first
  function checkSerial() {
    hideStepsFrom(["step3","step4","step5","step6","step7","step8"]);
    clearResult();
    const noteElem = document.getElementById("countryNote");
    noteElem.textContent = "";
    noteElem.classList.add("hidden");

    const caseId = (document.getElementById("caseId").value || "").trim();
    if (!caseId) {
      showResult("Please enter a Case ID before continuing.", false);
      document.getElementById("caseId").focus();
      return;
    }

    const serial = (document.getElementById("serialNumber").value || "").trim().toUpperCase();
    const ok = allowedPrefixes.some(function (p) { return serial.startsWith(p); });

    if (!serial) {
      showResult("Please enter a Serial Number.", false);
      document.getElementById("serialNumber").focus();
      return;
    }

    if (!ok) {
      showResult("We do not work on this case (unsupported serial number).", false);
      return;
    }

    showStep("step3");
    showResult("Serial number looks fine. Go to Country.", true);
    updateSummary();
  }

  // Step 3: Country + time rules
  function checkCountry() {
    hideStepsFrom(["step4","step5","step6","step7","step8"]);
    clearResult();

    const noteElem = document.getElementById("countryNote");
    noteElem.textContent = "";
    noteElem.classList.add("hidden");

    const country = document.getElementById("country").value;
    if (!country) return;

    const istTime = getCurrentISTTime();

    if (country === "OTHERS") {
      showStep("step4");
      showResult("Country selected as Other. Continue to Account check.", true);
      return;
    }

    // US: after 17:30 IST, Onshore
    if (country === "US" && isAfter(istTime, "17:30")) {
      noteElem.textContent =
        "Country is US and time is past 17:30 IST – Onshore will take this case.";
      noteElem.classList.remove("hidden");
    }

    // OBH: before 12:30 or after 21:30 IST
    if (obhCountries.includes(country) &&
        (isBefore(istTime, "12:30") || isAfter(istTime, "21:30"))) {
      noteElem.textContent =
        "OBH team will take care of the case. If you have a case with the above countries send to MFQ.";
      noteElem.classList.remove("hidden");
    }

    showStep("step4");
    showResult("Country selected. Continue to Account check.", true);
  }

  // Step 4: Public account
  function checkAccount() {
    hideStepsFrom(["step5","step6","step7","step8"]);
    clearResult();

    const value = document.getElementById("isPublicAccount").value;
    if (!value) return;

    if (value === "yes") {
      showResult("We do not work on this case (Public Account).", false);
      return;
    }

    showStep("step5");
    showResult("Account is not public. Continue to Case origin.", true);
  }

  // Step 5: Origin
  function checkOrigin() {
    hideStepsFrom(["step6","step7","step8"]);
    clearResult();

    const origin = document.getElementById("origin").value;
    if (!origin) return;

    showStep("step6");
    showResult("Origin captured. Check complexity / SFDC search.", true);
  }

  // Step 6: Complexity
  function checkComplex() {
    hideStepsFrom(["step7","step8"]);
    clearResult();

    const value = document.getElementById("complexIssue").value;
    const sfdcHint = document.getElementById("sfdcHint");
    if (!value) return;

    if (value === "yes") {
      sfdcHint.classList.remove("hidden");
    } else {
      sfdcHint.classList.add("hidden");
    }

    showStep("step7");
    showStep("step8");
    showResult(
      "We work on this case. Follow POA, initial email, troubleshooting, and delay update steps.",
      true
    );
  }

  // Summary helper
  function updateSummary() {
    const caseId = (document.getElementById("caseId").value || "").trim();
    const serial = (document.getElementById("serialNumber").value || "").trim();
    const country = document.getElementById("country").value || "";
    const account = document.getElementById("isPublicAccount").value || "";
    const origin = document.getElementById("origin").value || "";
    const complex = document.getElementById("complexIssue").value || "";
    const istTime = getCurrentISTTime();

    var lines = [];
    lines.push("Current IST time: " + istTime);
    lines.push("Case ID: " + (caseId || "-"));
    lines.push("Serial number: " + (serial || "-"));
    lines.push("Country: " + (country || "-"));
    lines.push("Account (Public?): " + (account || "-"));
    lines.push("Origin: " + (origin || "-"));
    lines.push("Complex / Phone/Chat: " + (complex || "-"));

    document.getElementById("summaryBox").value = lines.join("\n");
  }

  // initialise summary on load
  updateSummary();
</script>
</body>
</html>
