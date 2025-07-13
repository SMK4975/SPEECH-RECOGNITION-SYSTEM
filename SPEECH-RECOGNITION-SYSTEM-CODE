String command;

void setup() {
  Serial.begin(9600);
  pinMode(2, OUTPUT);  // LED1
  pinMode(3, OUTPUT);  // LED2
  Serial.println("Speech Command System Ready");
}

void loop() {
  if (Serial.available()) {
    command = Serial.readStringUntil('\n');
    command.trim();  // Remove leading/trailing spaces

    if (command == "light on") {
      digitalWrite(2, HIGH);
      Serial.println("Light turned ON");
    } 
    else if (command == "light off") {
      digitalWrite(2, LOW);
      Serial.println("Light turned OFF");
    } 
    else if (command == "fan on") {
      digitalWrite(3, HIGH);
      Serial.println("Fan turned ON");
    } 
    else if (command == "fan off") {
      digitalWrite(3, LOW);
      Serial.println("Fan turned OFF");
    } 
    else {
      Serial.println("Unknown command");
    }
  }
}
