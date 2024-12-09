<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Matin Topup - Mobile Legends</title>
  <style>
    body {
      font-family: 'Arial', sans-serif;
      margin: 0;
      padding: 0;
      background: #fafafa;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }

    .container {
      background: #fff;
      border-radius: 10px;
      box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
      width: 100%;
      max-width: 400px;
      padding: 30px;
      text-align: center;
      transition: transform 0.3s ease;
    }

    .container:hover {
      transform: scale(1.02);
    }

    .header {
      background-color: #ff66a3;
      color: white;
      padding: 20px;
      border-radius: 10px;
      font-size: 24px;
      font-weight: bold;
    }

    .form-group {
      margin-bottom: 20px;
      text-align: left;
    }

    .form-group label {
      font-size: 16px;
      color: #555;
      margin-bottom: 5px;
      display: block;
    }

    .form-group input {
      width: 100%;
      padding: 12px;
      font-size: 16px;
      border-radius: 8px;
      border: 1px solid #ddd;
      margin-top: 5px;
      color: #333;
      transition: border-color 0.3s;
    }

    .form-group input:focus {
      border-color: #ff66a3;
    }

    .button {
      background-color: #ff66a3;
      color: white;
      border: none;
      padding: 14px;
      font-size: 16px;
      border-radius: 8px;
      cursor: pointer;
      margin-top: 15px;
      width: 100%;
      transition: background-color 0.3s ease;
    }

    .button:hover {
      background-color: #ff3385;
    }

    .package-container {
      display: flex;
      justify-content: space-between;
      margin-top: 20px;
      flex-wrap: wrap;
    }

    .package {
      background-color: #ffe6f0;
      border: 1px solid #ff66a3;
      padding: 15px;
      border-radius: 8px;
      width: 48%;
      text-align: center;
      margin-bottom: 10px;
      cursor: pointer;
      transition: background-color 0.3s, transform 0.3s ease;
    }

    .package:hover {
      background-color: #ff66a3;
      color: white;
      transform: scale(1.05);
    }

    .package.selected {
      background-color: #ff66a3;
      color: white;
    }

    .telegram-btn {
      margin-top: 20px;
      background-color: #33b5e5;
    }

    .telegram-btn:hover {
      background-color: #0288d1;
    }

  </style>
</head>
<body>

  <div class="container">
    <div class="header">Matin Topup - Mobile Legends</div>

    <div class="form-group">
      <label for="userId">User ID</label>
      <input type="text" id="userId" placeholder="Enter your User ID">
    </div>

    <div class="form-group">
      <label for="zoneId">Zone ID</label>
      <input type="text" id="zoneId" placeholder="Enter your Zone ID">
    </div>

    <button class="button" onclick="checkId()">Check ID</button>

    <div class="package-container" id="packages-section" style="display: none;">
      <div class="package" onclick="selectPackage(this, 'Weekly Pass x1 - $1.49')">
        <p>Weekly Pass x1</p>
        <p>$1.49</p>
      </div>
      <div class="package" onclick="selectPackage(this, 'Weekly Pass x3 - $4.77')">
        <p>Weekly Pass x3</p>
        <p>$4.77</p>
      </div>
      <div class="package" onclick="selectPackage(this, 'Weekly Pass x5 - $7.45')">
        <p>Weekly Pass x5</p>
        <p>$7.45</p>
      </div>
      <div class="package" onclick="selectPackage(this, '172 DM + Weekly Pass - $4.28')">
        <p>172 DM + Weekly Pass</p>
        <p>$4.28</p>
      </div>
      <div class="package" onclick="selectPackage(this, 'Weekly Pass x3 - $4.77')">
        <p>257 DM+weekly</p>
        <p>$5.59</p>
    </div>
      <div class="package" onclick="selectPackage(this, 'Weekly Pass x3 - $4.77')">
        <p>11 Daimonds</p>
        <p>$0.25</p>
      </div>
      <div class="package" onclick="selectPackage(this, 'Weekly Pass x3 - $4.77')">
        <p>22 Daimonds</p>
        <p>$0.50</p>
      </div>
      <div class="package" onclick="selectPackage(this, 'Weekly Pass x3 - $4.77')">
        <p>56 Daimonds</p>
        <p>$0.97</p>
      </div>
      <div class="package" onclick="selectPackage(this, 'Weekly Pass x3 - $4.77')">
        <p>86 Daimonds</p>
        <p>$1.39</p>
      </div>
      <div class="package" onclick="selectPackage(this, 'Weekly Pass x3 - $4.77')">
        <p>172 Daimonds</p>
        <p>$2.79</p>
      </div>
      </div>
      
    <button class="button" onclick="submitDetails()">PayABA</button>
    <button class="telegram-btn button" onclick="goToTelegram()">Go to Telegram</button>
  </div>

  <script>
    let selectedPackage = '';
    let selectedPackageElement = null;

    function checkId() {
      const userId = document.getElementById("userId").value.trim();
      const zoneId = document.getElementById("zoneId").value.trim();

      if (!userId || !zoneId) {
        alert("Please fill in all fields: User ID and Zone ID.");
        return;
      }

      // Show the packages section after ID check
      document.getElementById("packages-section").style.display = 'flex';
    }

    function selectPackage(element, packageName) {
      // Deselect previously selected package
      if (selectedPackageElement) {
        selectedPackageElement.classList.remove('selected');
      }

      // Select the new package
      selectedPackageElement = element;
      selectedPackageElement.classList.add('selected');
      selectedPackage = packageName;
      alert(`Package selected: ${packageName}`);
    }

    function submitDetails() {
      // Check if a package is selected
      if (!selectedPackage) {
        alert("Please select a package before submitting.");
        return;
      }

      // Check if User ID and Zone ID are filled
      const userId = document.getElementById("userId").value.trim();
      const zoneId = document.getElementById("zoneId").value.trim();

      if (!userId || !zoneId) {
        alert("Please fill in all fields: User ID and Zone ID.");
        return;
      }

      // Redirect to the specified URL
      const gameUrl = "https://pay.ababank.com/pfSZ5LnXfYBKRFHd8"; // Link to the website
      window.location.href = gameUrl; // Redirect to the game page
    }

    function goToTelegram() {
      const telegramUrl = "https://t.me/MATIN0168"; // Replace with actual Telegram link
      window.location.href = telegramUrl;
    }
  </script>
