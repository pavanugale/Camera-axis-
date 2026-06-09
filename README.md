<!DOCTYPE html>
<html lang="mr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>कॅमेरा ॲक्सेस</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin-top: 50px;
        }
        video {
            width: 90%;
            max-width: 500px;
            border: 3px solid #333;
            border-radius: 10px;
            background-color: #000;
        }
        button {
            padding: 10px 20px;
            font-size: 16px;
            background-color: #28a745;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            margin-bottom: 20px;
        }
        button:hover {
            background-color: #218838;
        }
    </style>
</head>
<body>

    <h2>GitHub कॅमेरा ॲक्सेस प्रोजेक्ट</h2>
    
    <!-- कॅमेरा सुरू करण्याचे बटन -->
    <button onclick="startCamera()">कॅमेरा सुरू करा</button>
    <br>
    
    <!-- इथे कॅमेराचा व्हिडिओ दिसेल -->
    <video id="videoScreen" autoplay playsinline></video>

    <script>
        async function startCamera() {
            try {
                // युझरकडे कॅमेरा (व्हिडिओ) वापरण्याची परवानगी मागणे
                const stream = await navigator.mediaDevices.getUserMedia({ video: true });
                
                // व्हिडिओ स्क्रीनला कॅमेऱ्याचा प्रवाह (Stream) जोडणे
                const videoElement = document.getElementById('videoScreen');
                videoElement.srcObject = stream;
            } catch (error) {
                // जर युझरने परवानगी नाकारली किंवा कॅमेरा नसेल तर एरर दाखवणे
                alert("कॅमेरा ॲक्सेस नाकारला किंवा तुमच्या डिव्हाइसमध्ये कॅमेरा नाही!");
                console.error("Error accessing camera: ", error);
            }
        }
    </script>

</body>
</html>
