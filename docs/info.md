<!---

This file is used to generate your project datasheet. Please fill in the information below and delete any unused
sections.

You can also include images in this folder and reference them in the markdown. Each image must be less than
512 kb in size, and the combined size of all images must be less than 1 MB.
-->

## How it works

The first 4 flip-flops are used as synchronizers. Four states are defined: Full, Half1, Half2, and Empty. These four states are mapped to the binary codes 00, 01, 10, and 11, and are further linked to 4 LEDs. The logic circuit is designed to control the states using D flip-flops. Additionally, another logic circuit is implemented with the help of one D flip-flop to control the motor. The motor only turns on when the system reaches the last stage (Empty) and turns off only when the water level in the tank is Full.

## How to test


The system has **3 inputs**:  
- **Clock**  
- **Input A**  
- **Input B**  

And a total of **5 outputs**:  
- **Out1**: Connected to a red LED (Full).  
- **Out2**: Connected to a yellow1 LED (Half1).  
- **Out3**: Connected to a yellow2 LED (Half2).  
- **Out4**: Connected to a red LED (Empty).  
- **Out5**: Connected to a red LED (Motor).  

---

### **Testing Table:**  

| **Clock** | **Input A** | **Input B** | **Out-1** | **Out-2** | **Out-3** | **Out-4** | **Out-5** |  
|-----------|-------------|-------------|-----------|-----------|-----------|-----------|-----------|  
| 5-5k     | 0           | 0           | 1         | 0         | 0         | 0         | 0         |  
| 5-5k     | 0           | 1           | 0         | 1         | 0         | 0         | 0         |  
| 5-5k     | 1           | 0           | 0         | 0         | 1         | 0         | 0         |  
| 5-5k     | 1           | 1           | 0         | 0         | 0         | 1         | 1         |  
| 5-5k     | 1           | 0           | 0         | 0         | 1         | 0         | 1         |  
| 5-5k     | 0           | 1           | 0         | 1         | 0         | 0         | 1         |  
| 5-5k     | 0           | 0           | 1         | 0         | 0         | 0         | 0         |  

---

### **Explanation of the Testing Table:**  
1. **Clock Signal (5-5k):**  
   - A clock signal with a frequency of 5 kHz is applied to synchronize the system.  

2. **Input Combinations (A and B):**  
   - The inputs **A** and **B** are varied to simulate different states of the system.  

3. **Output Behavior:**  
   - **Out-1 (Red LED - Full):** Turns on (1) only when both inputs are **0-0**.  
   - **Out-2 (Yellow1 LED - Half1):** Turns on (1) when inputs are **0-1**.  
   - **Out-3 (Yellow2 LED - Half2):** Turns on (1) when inputs are **1-0**.  
   - **Out-4 (Red LED - Empty):** Turns on (1) when inputs are **1-1**.  
   - **Out-5 (Red LED - Motor):** Turns on (1) when the system is in the **Empty** state (1-1) or during specific intermediate states (e.g., 1-0 or 0-1).  

4. **Sequence Matters:**  
   - The order of input combinations is critical to ensure proper state transitions and correct operation of the system.  

---

This table and explanation provide a clear guide for testing the system, ensuring that the outputs correspond correctly to the input combinations and sequence.t

## External hardware

1. Visual Indicators (LEDs):
Red LED (Full): To indicate when the tank is full.

Yellow1 LED (Half1): To indicate the first "half-full" state.

Yellow2 LED (Half2): To indicate the second "half-full" state.

Red LED (Empty): To indicate when the tank is empty.

Red LED (Motor): To indicate the motor's state (on/off).

2. Motor:
DC Motor: To pump water and fill the tank.

