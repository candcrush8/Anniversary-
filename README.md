# <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Anniversary Surprise</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <audio id="bgMusic" autoplay loop>
        <source src="your-song.mp3" type="audio/mp3">
    </audio>

    <div id="slide-container">
        <div class="slide" id="slide1">
            <h1>Something Special for You, Urooz! 💖</h1>
            <button class="heart-btn" onclick="nextSlide()">Continue</button>
        </div>

        <div class="slide" id="slide2">
            <h2>A Very Special Day...</h2>
            <button class="heart-btn" onclick="nextSlide()">Continue</button>
        </div>

        <div class="slide" id="slide3">
            <h2>15/05/2023 ✨</h2>
            <button class="heart-btn" onclick="nextSlide()">Continue</button>
        </div>

        <div class="slide" id="slide4">
            <div class="envelope" onclick="showMessage('msg1')">
                <p>Click the envelope ✉️</p>
            </div>
            <div class="hidden-message" id="msg1">
                <p>Two years, countless memories, endless love. ❤️ Every day apart only makes me cherish you more. ✨ Distance may separate us, but our hearts beat as one. 💞 You are my peace, my joy, my forever. 💖 Happy Anniversary, my love.</p>
            </div>
            <button class="heart-btn" onclick="nextSlide()">Continue</button>
        </div>

        <div class="slide" id="slide5">
            <div class="envelope" onclick="showMessage('msg2')">
                <p>फिर से क्लिक करें ✉️</p>
            </div>
            <div class="hidden-message" id="msg2">
                <p>दो साल का प्यार, दो साल का सफर, दो साल की अनमोल यादें। ❤️ तेरी हंसी मेरी खुशी, तेरा प्यार मेरी दुनिया। ✨ दूरियाँ हमारे दिलों को और करीब लाती हैं। 💞 हर पल, हर धड़कन, बस तुझसे जुड़ी है। 💖 शुभ वर्षगांठ, मेरी जान!</p>
            </div>
            <button class="heart-btn" onclick="nextSlide()">Continue</button>
        </div>

        <div class="slide" id="slide6">
            <h2>Guess my birthdate! 🎂</h2>
            <input type="text" id="birthdateGuess" placeholder="Enter your guess">
            <button onclick="checkGuess('birthdateGuess', '25/05/2006', 'hint1')">Submit</button>
            <button onclick="showHint('hint1')">Hint?</button>
            <p id="hint1" class="hidden-hint">Hint: It's in May! 🌼</p>
            <button class="heart-btn" onclick="nextSlide()">Continue</button>
        </div>

        <div class="slide" id="slide7">
            <h2>Where did we first meet? ☕</h2>
            <input type="text" id="placeGuess" placeholder="Enter your answer">
            <button onclick="checkGuess('placeGuess', 'Purple Cafe', 'hint2')">Submit</button>
            <button onclick="showHint('hint2')">Hint?</button>
            <p id="hint2" class="hidden-hint">Hint: It's a cozy café! ☕</p>
            <button class="heart-btn" onclick="nextSlide()">Continue</button>
        </div>

        <div class="slide" id="slide8">
            <h2>Solve this puzzle! 🧩</h2>
            <canvas id="puzzleCanvas"></canvas>
            <button onclick="shufflePuzzle()">Shuffle Pieces</button>
            <button onclick="showHint('hint3')">Hint?</button>
            <p id="hint3" class="hidden-hint">Hint: Just arrange the pieces! 🖼️</p>
            <button class="heart-btn" onclick="nextSlide()">Continue</button>
        </div>

        <div class="slide" id="slide9">
            <h2>🎉 You did it! 🎉</h2>
            <div class="love-animation">💖 Love You So Much, Urooz 💖</div>
            <button class="heart-btn" onclick="nextSlide()">Continue</button>
        </div>

        <div class="slide rotating-images" id="slide10">
            <h2>Our Beautiful Journey 📸</h2>
            <img src="pic1.jpg" alt="Picture 1">
            <img src="pic2.jpg" alt="Picture 2">
            <img src="pic3.jpg" alt="Picture 3">
            <button class="heart-btn" onclick="nextSlide()">Continue</button>
        </div>

        <div class="slide" id="slide11">
            <h2>💖 Tm & Urooz 💖</h2>
            <button class="heart-btn" onclick="nextSlide()">Continue</button>
        </div>

        <div class="slide" id="slide12">
            <h2>Want to relive the magic? ✨</h2>
            <button class="heart-btn" onclick="replay()">Replay</button>
        </div>
    </div>

    <script src="script.js"></script>
</body>
</html>
id="slide2">
            <h2>A
            let currentSlide = 1;

function nextSlide() {
    let slides = document.querySelectorAll('.slide');
    slides[currentSlide - 1].style.display = "none";
    currentSlide++;
    if (currentSlide <= slides.length) {
        slides[currentSlide - 1].style.display = "block";
    }
}

function showMessage(id) {
    document.getElementById(id).style.display = "block";
}

function checkGuess(inputId, correctValue, hintId) {
    let userInput = document.getElementById(inputId).value.trim();
    if (userInput.toLowerCase() === correctValue.toLowerCase()) {
        alert("Correct! 🎉");
    } else {
        alert("Try again!");
        document.getElementById(hintId).style.display = "block";
    }
}

function showHint(id) {
    document.getElementById(id).style.display = "block";
}

function replay() {
    location.reload();
}

// Puzzle Interaction
const canvas = document.getElementById("puzzleCanvas");
const ctx = canvas.getContext("2d");

let pieces = []; 

function shufflePuzzle() {
    pieces.sort(() => Math.random() - 0.5);
    drawPuzzle();
}

function drawPuzzle() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    pieces.forEach((piece, index) => {
        ctx.drawImage(piece.image, piece.x, piece.y, piece.width, piece.height);
    });
}

// Initialize Puzzle (Replace with real image URL)
const image = new Image();
image.src = "your-image.jpg";
image.onload = function () {
    for (let i = 0; i < 4; i++) {
        for (let j = 0; j < 4; j++) {
            let piece = {
                image: image,
                x: i * 50,
                y: j * 50,
                width: 50,
                height: 50
            };
            pieces.push(piece);
        }
    }
    shufflePuzzle();
};
