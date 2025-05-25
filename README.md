<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>IMEI Phone Model Checker</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            max-width: 600px;
            margin: 0 auto;
            padding: 20px;
            background-color: #f5f5f5;
        }
        .container {
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        h1 {
            color: #333;
            text-align: center;
        }
        .input-group {
            margin-bottom: 20px;
        }
        label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }
        input[type="text"] {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 16px;
        }
        button {
            background-color: #4CAF50;
            color: white;
            border: none;
            padding: 10px 15px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
            width: 100%;
        }
        button:hover {
            background-color: #45a049;
        }
        #result {
            margin-top: 20px;
            padding: 15px;
            border-radius: 4px;
            display: none;
        }
        .valid {
            background-color: #dff0d8;
            color: #3c763d;
        }
        .invalid {
            background-color: #f2dede;
            color: #a94442;
        }
        .info {
            margin-top: 30px;
            font-size: 14px;
            color: #666;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Phone Model IMEI Checker</h1>
        
        <div class="input-group">
            <label for="imei">Enter IMEI Number (15 digits):</label>
            <input type="text" id="imei" placeholder="e.g., 123456789012345" maxlength="15">
        </div>
        
        <button onclick="checkIMEI()">Check Phone Model</button>
        
        <div id="result"></div>
        
        <div class="info">
            <p><strong>How to find your IMEI:</strong></p>
            <ul>
                <li>Dial *#06# on your phone</li>
                <li>Check in Settings > About Phone > Status</li>
                <li>Look on the original box or under the battery</li>
            </ul>
            <p><strong>Note:</strong> This is a basic demonstration. For detailed information, please use official IMEI checking services.</p>
        </div>
    </div>

    <script>
        function checkIMEI() {
            const imei = document.getElementById('imei').value.trim();
            const resultDiv = document.getElementById('result');
            
            // Clear previous results
            resultDiv.style.display = 'none';
            
            // Validate IMEI format
            if (!imei || imei.length !== 15 || !/^\d+$/.test(imei)) {
                resultDiv.className = 'invalid';
                resultDiv.innerHTML = '<strong>Invalid IMEI:</strong> Please enter a valid 15-digit IMEI number.';
                resultDiv.style.display = 'block';
                return;
            }
            
            // This is a simulation - in a real app you would call an API here
            simulateIMEICheck(imei, resultDiv);
        }
        
        function simulateIMEICheck(imei, resultDiv) {
            // This is a simulation - in a real app you would call an actual IMEI database API
            
            // Show loading state
            resultDiv.className = '';
            resultDiv.innerHTML = 'Checking IMEI database...';
            resultDiv.style.display = 'block';
            
            // Simulate API delay
            setTimeout(function() {
                // This is just sample data - in reality you would get this from an API
                const manufacturers = ['Apple', 'Samsung', 'Huawei', 'Xiaomi', 'Oppo', 'Vivo', 'OnePlus'];
                const models = {
                    'Apple': ['iPhone 15', 'iPhone 14', 'iPhone 13', 'iPhone 12'],
                    'Samsung': ['Galaxy S23', 'Galaxy S22', 'Galaxy A54', 'Galaxy Note 20'],
                    'Huawei': ['P50 Pro', 'Mate 40', 'Nova 9'],
                    'Xiaomi': ['Redmi Note 12', 'Mi 11', 'Poco X5'],
                    'Oppo': ['Find X5', 'Reno 8'],
                    'Vivo': ['X80', 'V25'],
                    'OnePlus': ['11', '10 Pro']
                };
                
                // Generate random but consistent results based on IMEI
                const manufacturer = manufacturers[parseInt(imei[0]) % manufacturers.length];
                const model = models[manufacturer][parseInt(imei[1]) % models[manufacturer].length;
                const productionDate = `202${imei[2] % 3 + 1}-${imei[3] % 12 + 1}`;
                const country = ['China', 'Vietnam', 'India', 'Brazil', 'Indonesia'][imei[4] % 5];
                
                resultDiv.className = 'valid';
                resultDiv.innerHTML = `
                    <h3>IMEI: ${imei}</h3>
                    <p><strong>Manufacturer:</strong> ${manufacturer}</p>
                    <p><strong>Model:</strong> ${model}</p>
                    <p><strong>Production Date:</strong> ${productionDate}</p>
                    <p><strong>Production Country:</strong> ${country}</p>
                    <p><em>Note: This is simulated data. For real information, use official IMEI checking services.</em>
                `;
                resultDiv.style.display = 'block';
            }, 1500);
        }
    </script>
</body>
</html>
