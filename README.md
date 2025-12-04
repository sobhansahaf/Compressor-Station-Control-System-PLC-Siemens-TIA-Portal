# Compressor Station Control System – PLC Program (TIA Portal)

This project describes the control logic of a **Compressor Station** implemented in **Siemens TIA Portal**.
The system includes **four motors**, **PT100 temperature sensors**, a **pressure transmitter**, and a **pneumatic control valve**. Motors **2** and **4** operate as **standby units**.

---

## 🔧 System Components

* **Motors (M1, M2, M3, M4)**

  * M2 and M4 function as standby (reserve) motors.
* **PT100 Temperature Sensors**

  * One installed on each motor for temperature monitoring.
* **Pressure Transmitter**

  * Measures the pressure of the Compressor Station.
* **Control Valve**

  * Directs compressed air into the workshop when needed.
* **Start /  Stop Push Buttons**

---

## 🚀 Operation Logic

###  Start Sequence

When the **Start** button is pressed:

* **Motor 1 (M1)** starts.
* If the Compressor Station pressure is **below 3 bar**, ** Motor 3 (M3)** also starts.

---

## 🌡 Temperature Control Logic

### 🔥 Overtemperature Protection

If the temperature of **M1 or M3** exceeds **80°C**:

* The overheated motor **shuts down**.
* The corresponding **Temperature Fault Signal** activates.
* The related **standby motor** starts automatically if its temperature is **below 75°C**:

  * M1 overheated → M2 may start
  * M3 overheated → M4 may start

###  Re-enabling Main Motors

If a main motor cools down **below 75°C**:

* It will **not** automatically restart.
* The operator must press a **Confirmation Push Button** to bring it back into operation.

---

## 📈 Pressure Control Logic

If the Compressor Station pressure rises **above 8 bar**:

* The **High Pressure Alarm** turns on.
* **Motor 3 (M3)** shuts down.
* The **Control Valve** opens, directing compressed air into the workshop.

---

## ⛔ Stop Logic

Pressing the **Stop** button:

* Turns **OFF all motors**.
* Closes the **control valve**.


