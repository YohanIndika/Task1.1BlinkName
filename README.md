# Task1.1BlinkName
Assignment 1 Blinking the first name in morse code

const int dotTime = 200;  // duration of a dot
const int dashTime = dotTime * 3;  // duration of a dash
const int symbolSpace = dotTime;  // space between symbols within a letter
const int letterSpace = dotTime * 3;  // space between letters
const int wordSpace = dotTime * 7;  // space between words

void setup() {
  // initialize digital pin LED_BUILTIN as an output.
  pinMode(LED_BUILTIN, OUTPUT);
}

// Function to blink a dot
void blinkDot() {
  digitalWrite(LED_BUILTIN, HIGH);
  delay(dotTime);
  digitalWrite(LED_BUILTIN, LOW);
  delay(symbolSpace);
}

// Function to blink a dash
void blinkDash() {
  digitalWrite(LED_BUILTIN, HIGH);
  delay(dashTime);
  digitalWrite(LED_BUILTIN, LOW);
  delay(symbolSpace);
}

// Function to blink a Morse code character
void blinkMorseChar(char c) {
  switch (c) {
    case 'Y': blinkDash(); blinkDot(); blinkDash(); blinkDash(); break;
    case 'O': blinkDash(); blinkDash(); blinkDash(); break;
    case 'H': blinkDot(); blinkDot(); blinkDot(); blinkDot(); break;
    case 'A': blinkDot(); blinkDash(); break;
    case 'N': blinkDash(); blinkDot(); break;
  }
}

void loop() {
  char name[] = "YOHAN";

  for (int i = 0; i < sizeof(name) - 1; i++) {
    blinkMorseChar(name[i]);
    if (i < sizeof(name) - 2) {
      delay(letterSpace - symbolSpace);  // space between letters
    }
  }

  delay(wordSpace - letterSpace);  // space between words before repeating
} 
