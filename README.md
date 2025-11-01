# Bluetooth controlled RC-Car
A DIY Bluetooth-controlled RC car project using **Arduino Uno**, designed to demonstrate wireless motor control and embedded systems fundamentals.  
This project helps beginners understand **DC motor control**, **PWM**, and **serial communication** via Bluetooth.

# Features
- Wireless control using a smartphone app (HC-05 Bluetooth module)
- Forward, backward, left, and right motion control
- Speed control via PWM
- Easy to assemble and modify
- Powered by rechargeable Li-ion battery


# Component Used
| Component | Description |
|------------|--------------|
| Arduino Uno | Main microcontroller |
| L298N Motor Driver | Controls two DC motors |
| HC-05 Bluetooth Module | Enables wireless communication |
| DC Motors (x2) | Drive the car |
| Li-ion Battery | Power source |
| Chassis + Wheels | Body frame |
| Jumper Wires | Connections |



#
char data;//variable to store recieved data

void setup(){
    serial.begin(9600);//start serial communication at 9600 baud rate

    //set motor control pins as output
    pinMode(7,OUTPUT);
    pinMode(6,OUTPUT);
    pinMode(5,OUTPUT);
    pinMode(4,OUTPUT);


}

void loop() {
    if (serial.available()>0) {
        data = serial.read();//Read recieved data

        //Control motor movement based on recieved data 
        switch(data){
            case 'F'://Move Forward
            digitalWrite(7,High);
            digitalWrite(6,Low);
            digitalWrite(5,High);
            digitalWrite(4,Low);
            break;
            case 'B'://Move Backward
            digitalwrite(6,High);
            digitalwrite(5,Low);
            digitalwrite(4,High);
            break;
            case 'R'://Turn Right
            digitalwrite(7,Low);
            digitalwrite(6,High);
            digitalwrite(5,High);
            digitalwrite(4,Low);
            break;
            case 'L':// Turn Left
            digitalwrite(7,High);
            digitalwrite(6,Low);
            digitalwrite(5,Low);
            digitalwrite(4,Low);
            break;
            case 'S'://Stop
            digitalwrite(7,Low);
            digitalwrite(6,Low);
            digitalwrite(5,Low);
            digitalwrite(4,Low);
            break;

        }
    }
}


# How to Use
1. Upload `rc_car_bluetooth.ino` to Arduino Uno using the **Arduino IDE**.
2. Pair your phone with the **HC-05 Bluetooth module** (`Password: 1234` or `0000`).
3. Use any Bluetooth terminal or RC car controller app.
4. Send commands:
   - `F` → Forward  
   - `B` → Backward  
   - `L` → Left  
   - `R` → Right  
   - `S` → Stop  


## setup and installation 
1. Clone this repository
'''bash
git clone https://github.com/<nitish-codes>/rc-car-bluetooth-arduino.git