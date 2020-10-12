# NumberGuessGame
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">

    <title>Number guessing game</title>

    <style>
      html {
        font-family: sans-serif;
      }

      body {
        width: 80%;
        max-width: 800px;
        min-width: 400px;
        margin: 0 auto;
      }

      .lastResult {
        color: white;
        padding: 3px;
      }
    </style>
    
  </head>

  <body>
    <h1>Number guessing game</h1>

    <p>We have selected a random number between 1 and 100. See if you can guess it in 10 turns or fewer. We'll tell you if your guess was too high or too low.</p>

    <div class="form">
      <label for="guessField">Enter a guess: </label>
      <input type="text" id="guessField" class="guessField">
      <input type="submit" value="Submit guess" class="guessSubmit">
    </div>

    <div class="resultParas">
      <p class="guesses"></p>
      <p class="lastResult"></p>
      <p class="lowOrHi"></p>
    </div>

<script>
let userName = prompt('Enter your Name');
let randomNumber = Math.floor(Math.random() * 100) + 1;
        
        const guesses = document.querySelector('.guesses');
        const lastResult = document.querySelector('.lastResult');
        const lowOrHi = document.querySelector('lowOrHi');
        
        const guessField = document.querySelector('.guessField');
        const guessSubmit = document.querySelector('.guessSubmit');
        
        let guesssCount = 0;
        let resetButton;
        
        function checkGuess() {
        let userGuess = Number(guessField.Value);
        if (guesssCount === 1){
        guesses.textContent = 'Previous Guesses:';
        }
        guesses.textContent += userGuess + ' ';
        
        if (userGuess === randomNumber){
            lastResult.textContent = 'Congratulations! you got it right';
            lastResult.style.backgroundColor = 'green';
            lowOrHi.textContent = '';
            startGameOver();
        } else if (guesssCount === 10){
            lastResult.textContent = '!!! Game Over !!!'
            setGameOver();
        }else {
            lastResult.textContent = 'Wrong';
            lastResult.style.backgroundColor = 'red';
        }
        if (userGuess < randomNumber){
                lowOrHi.textContent = 'Last guess was too low';
            }
            else if (userGuess > randomNumber) {
                    lowOrHi.textContent = 'Last guess was too hight';
                }
        }
        
            guesssCount++;
            guessField.Value = 'blue';
            guessField.focus();
        
    guessSubmit.addEventListener('click', checkGuess);
        
        function setGameOver() {
            guessField.disabled = true;
            guessSubmit.disabled = true;
            resetButton = document.createElement('Button');
            resetButton.textContent = 'Start new Game';
            documnet.body.append(resetButton);
            resetButton.addEventListener('click' , resetGame);
        }
        
        function resetGame() {
            guesssCount = 1;
        
            const resetParas = document.querySelectorAll('.resultParas p');
        
            for (let i = 0; i < resetParas; i++){
                resetParas[i].textContent = '';
            }
        
            guessField.disabled = false;
            guessSubmit.disabled = false;
            guessField.Value = '';
            guessField.focus();
        
            lastResult.style.backgroundColor =  'white';
        
            randomNumber = Math.floor(Math.random() * 100) + 1;
        }
</script>
    </body>







    </html>
