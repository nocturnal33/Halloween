# Nathan Carlson
# 10/2/2023
# Arduino Mega
# This is to light up 10 Eyes, laser cut into a wooden board.
# 2 LEDs per eye and a third White LED to strobe

const int numLEDs = 20; // Number of LEDs
int ledPins[numLEDs] = {2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21}; // Pins where LEDs are connected
const int strobeLEDs = 10; // Strobing LEDs
int strobeAll[strobeLEDs] = {22, 23, 24, 24, 26, 27, 28, 29, 20, 31};
int ledRandOn;
int ledRandOff;
int cycleRand;
int cycle = 0;
int strobeCount;
int strobeDelayVal = 100;
int AllOnDelay = 50;

void setup() {
  // set up Color LEDs
  for (int i = 0; i < numLEDs; i++) {
    pinMode(ledPins[i], OUTPUT);
  }
  randomSeed(analogRead(0)); // Initialize random number generator with a seed

  // set up Strobe LEDS
  for (int i = 0; i < strobeLEDs; i++){
    pinMode(strobeAll[i], OUTPUT);
  }
}

void loop() {
  cycle = 0;  // Reset Cycle
  shuffleArray(ledPins, numLEDs); // Shuffle the LED pins array
  cycleRand = random(5, 20);
  // Turn on each LED in the shuffled order with a delay
  while(cycle < cycleRand){
    ledRandOn = random(1000, 8000);
    ledRandOff = random(500, 2000);
    for (int i = 0; i < numLEDs; i++) {
      digitalWrite(ledPins[i], HIGH); // Turn on LED
      delay(ledRandOn); 
      digitalWrite(ledPins[i], LOW); // Turn off LED
      delay(ledRandOff);
      cycle++;
    }
  }
  // start the stobe lights!!
  strobeCount = random(5, 20);
  for(int i = 0;i < strobeCount; i++){
    strobeLights();
  }
  for(int i = 0; i < 5; i++){
    strobeAllAtOnce();
  }
}

// Function to shuffle an array
void shuffleArray(int *array, int size) {
  for (int i = size - 1; i > 0; i--) {
    int j = random(i + 1); // Generate a random index
    // Swap array[i] and array[j]
    int temp = array[i];
    array[i] = array[j];
    array[j] = temp;
  }
}

void strobeLights() {
    for (int i = 0; i < numLEDs; i++) {
      digitalWrite(ledPins[i], HIGH);
    }
    delay(strobeDelayVal);
    for (int i = 0; i < numLEDs; i++) {
      digitalWrite(ledPins[i], LOW);
    }
    delay(strobeDelayVal);
    
    for (int i = 0; i < strobeLEDs; i++) {
      digitalWrite(ledPins[i], HIGH);
    }
    delay(strobeDelayVal);
    for (int i = 0; i < strobeLEDs; i++) {
      digitalWrite(ledPins[i], LOW);
    }
    delay(strobeDelayVal);
}

void strobeAllAtOnce(){
    for (int i = 0; i < numLEDs; i++) {
    digitalWrite(ledPins[i], HIGH);
    }
    delay(AllOnDelay);

    for (int i = 0; i < strobeLEDs; i++) {
      digitalWrite(ledPins[i], HIGH);
    }
    delay(AllOnDelay);

    for (int i = 0; i < numLEDs; i++) {
      digitalWrite(ledPins[i], LOW);
    }
    delay(AllOnDelay);
    

    for (int i = 0; i < strobeLEDs; i++) {
      digitalWrite(ledPins[i], LOW);
    }
    delay(AllOnDelay);
}



