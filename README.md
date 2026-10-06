<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Something For You ❤️</title>

<style>
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    font-family: Georgia, "Times New Roman", serif;
    background: linear-gradient(135deg, #120811, #351329, #160912);
    color: white;
    min-height: 100vh;
    overflow: hidden;
}

#lockScreen {
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 25px;
    text-align: center;
}

.lock-box {
    width: 100%;
    max-width: 400px;
    padding: 35px 25px;
    border-radius: 28px;
    background: rgba(255,255,255,0.08);
    border: 1px solid rgba(255,255,255,0.15);
    backdrop-filter: blur(15px);
    box-shadow: 0 20px 50px rgba(0,0,0,0.4);
    animation: appear 1s ease;
}

.lock-icon {
    font-size: 65px;
    margin-bottom: 20px;
    animation: pulse 1.8s infinite;
}

h1 {
    font-size: 30px;
    margin-bottom: 12px;
}

.subtitle {
    color: #eacbd7;
    line-height: 1.6;
    margin-bottom: 25px;
}

.code-input {
    width: 100%;
    padding: 16px;
    border-radius: 15px;
    border: 1px solid rgba(255,255,255,0.2);
    background: rgba(0,0,0,0.25);
    color: white;
    text-align: center;
    font-size: 25px;
    letter-spacing: 10px;
    outline: none;
}

.code-input:focus {
    border-color: #ff6d99;
    box-shadow: 0 0 15px rgba(255,70,120,.25);
}

button {
    width: 100%;
    padding: 15px;
    margin-top: 20px;
    border: none;
    border-radius: 25px;
    background: linear-gradient(135deg, #ff5c8a, #ff2f68);
    color: white;
    font-size: 17px;
    font-weight: bold;
    box-shadow: 0 8px 25px rgba(255,47,104,.3);
}

#error {
    color: #ff8cae;
    margin-top: 15px;
    min-height: 22px;
    font-size: 14px;
}

.hint {
    margin-top: 22px;
    font-size: 13px;
    color: #bfaab3;
}

#app {
    display: none;
}

@keyframes appear {
    from {
        opacity: 0;
        transform: translateY(25px) scale(.95);
    }

    to {
        opacity: 1;
        transform: translateY(0) scale(1);
    }
}

@keyframes pulse {
    0%,100% {
        transform: scale(1);
    }

    50% {
        transform: scale(1.12);
    }
}

.shake {
    animation: shake .4s;
}

@keyframes shake {
    0%,100% { transform: translateX(0); }
    25% { transform: translateX(-8px); }
    75% { transform: translateX(8px); }
}
</style>
</head>

<body>

<!-- SECRET CODE SCREEN -->

<div id="lockScreen">

    <div class="lock-box" id="lockBox">

        <div class="lock-icon">🔐</div>

        <h1>Something For You</h1>

        <p class="subtitle">
            I made something special for you.
            But there's one little thing you need
            before you can open it. ❤️
        </p>

        <input
            id="code"
            class="code-input"
            type="password"
            inputmode="numeric"
            maxlength="4"
            placeholder="••••"
            autocomplete="off"
        >

        <button onclick="unlock()">
            Unlock My Heart ❤️
        </button>

        <div id="error"></div>

        <p class="hint">
            Hint: It's a date that's special to me. 🥹
        </p>

    </div>

</div>


<!-- YOUR ROMANTIC APP STARTS HERE -->

<div id="app">

    <!--
        PUT THE REST OF YOUR ORIGINAL APP HERE.

        Start with:

        <section class="screen active">
        
        ...
        
    -->

</div>


<script>

function unlock() {

    const code = document.getElementById("code").value;
    const lockScreen = document.getElementById("lockScreen");
    const lockBox = document.getElementById("lockBox");
    const error = document.getElementById("error");
    const app = document.getElementById("app");

    // SECRET CODE
    if (code === "0417") {

        error.textContent = "";

        lockBox.style.transition = "all .8s ease";
        lockBox.style.transform = "scale(1.1)";
        lockBox.style.opacity = "0";

        setTimeout(() => {

            lockScreen.style.display = "none";
            app.style.display = "block";

            document.body.style.overflow = "auto";

        }, 800);

    } else {

        error.textContent =
            "That's not the code... try again, baby. 🥹";

        lockBox.classList.remove("shake");

        void lockBox.offsetWidth;

        lockBox.classList.add("shake");

        document.getElementById("code").value = "";

    }
}


// Allow pressing Enter instead of tapping the button

document.getElementById("code").addEventListener(
    "keydown",
    function(event) {

        if (event.key === "Enter") {
            unlock();
        }

    }
);

</script>

</body>
</html>