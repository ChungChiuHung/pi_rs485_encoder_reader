# pi_rs485_encoder_reader

# Encoder Documentation - [BRT38-R0M40960RT1](https://www.briter.net/%e4%b8%8b%e8%bd%bd%e4%b8%ad%e5%bf%83)

[說明書](https://www.briter.net/wp-content/uploads/2024/07/001-RS485%E8%AF%B4%E6%98%8E%E4%B9%A6%E9%80%9A%E4%BF%A1%E5%8D%8F%E8%AE%AE-%E5%8D%95%E5%9C%88-V2.4.pdf) <br>
[軟體](https://www.briter.net/wp-content/uploads/2024/11/05-RS485%E4%B8%8A%E4%BD%8D%E6%9C%BAV3.09-%E5%8D%95%E5%9C%88%E5%A4%9A%E5%9C%88-1.tar)<br>



This repository contains documentation and resources for the **BRT38-R0M40960RT1** rotary encoder (Absolute).

## Specifications

- **Model:** BRT38-R0M40960RT1
- **Type:** Rotary Encoder (Absolute)

## Wiring Diagram

| **Wire Color** | **Connection**                     |
| -------------- | ---------------------------------- |
| **Red**        | 5~24V (Power Supply)               |
| **White**      | 485A (Differential Signal A)       |
| **Green**      | 485B (Differential Signal B)       |
| **Yellow**     | ZR (Reference Signal)              |
| **Black**      | 0V (Ground)                        |

## ZR (Zero Reference) Signal

The ZR signal is typically used as an index pulse to mark a specific, known position in the encoder's rotation — often referred to as the "Home" or zero position. Here's how you can use the ZR signal to set the absolute position:

1. **Connect the ZR Signal:**  
   Wire the yellow output to a digital input on your controller (usually via an **interrupt** or polling mechanism).

2. **Monitor for the ZR Pulse:**  
   Since the ZR pulse occurs once per full rotation, configure your system to detect its rising (or falling) edge. This pulse represents a fixed and repeatable reference point.

3. **Calibrate the Position:**  
   When your system detects the ZR pulse, reset or set your position counter to a known value (commonly zero). This step establishes the starting absolute position for subsequent measurements.

4. **Maintain Accuracy:**  
   After setting the reference, all subsequent encoder readings are measured relative to this calibrated zero point. This helps maintain the accuracy of the absolute position data as the encoder continues to rotate.

5. **Periodic Recalibration (Optional):**  
   In some applications, the ZR pulse can be used for periodic recalibration, ensuring that any drift or errors in the counting mechanism are corrected regularly.
