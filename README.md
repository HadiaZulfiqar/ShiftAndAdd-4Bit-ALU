<h1>Shift and Add 4-Bit ALU Simulation</h1>

Multisim simulation of a 4-bit Arithmetic Logic Unit (ALU) utilizing bidirectional universal shift registers for dynamic input generation, a full-adder IC for binary addition, and a BCD-to-7-segment display driver.

<h2>Simulation</h2>
<img width="995" height="497" alt="image" src="https://github.com/user-attachments/assets/1690f3af-0687-4358-b2ba-9d89593f4dfb" />

<h2>explanation</h2>

<h3>Overview</h3>
<p>
This project demonstrates the design and simulation of a shift-and-add arithmetic unit[cite: 52]. The circuit generates two 4-bit binary operands dynamically using dual 4-bit universal shift registers configured for simultaneous right and left shifting[cite: 52, 60]. These operands are fed into a 4-bit full-adder IC, with the resulting sum routed through a BCD-to-7-segment decoder and displayed on a 7-segment monitor, while carry-out bits are monitored via an LED probe[cite: 52, 60].
</p>

<h3>Circuit Architecture & Components</h3>
<ul>
  <li><b>Universal Bidirectional Shift Registers (74LS194D)[cite: 53]:</b> Two ICs handle input generation[cite: 60]. The first register performs a Shift Right operation ($S_0=1, S_1=0$), while the second performs a Shift Left operation ($S_0=0, S_1=1$) based on mode control inputs[cite: 60].</li>
  <li><b>4-Bit Full-Adder IC (74283 / 7483N)[cite: 53]:</b> Combines the 4-bit outputs from both shift registers on every clock pulse, producing a 4-bit sum along with a carry-out indicator[cite: 52, 60].</li>
  <li><b>BCD-to-7-Segment Decoder (74LS47D)[cite: 53]:</b> Decodes the binary output values into standard decimal formatting for the display.</li>
  <li><b>Output Peripherals:</b> Includes a yellow common-anode 7-segment display, digital green/blue state probes for register outputs, and a red indicator probe for the carry-out ($C_4$) signal[cite: 53, 60].</li>
</ul>

<h3>Multisim Simulation & Functional Pulses</h3>
<p>
The system executes cumulative shift-and-add operations across sequential clock pulses:
</p>
<ul>
  <li><b>First Pulse:</b> Right shift register outputs $0001_2$ ($1_{10}$) and left shift register outputs $1000_2$ ($8_{10}$), resulting in a sum of $9_{10}$ shown directly on the 7-segment display with a zero carry[cite: 57, 58, 62].</li>
  <li><b>Second Pulse:</b> Inputs shift to $0011_2$ ($3_{10}$) and $1100_2$ ($12_{10}$), summing to $15_{10}$[cite: 58, 62].</li>
  <li><b>Third Pulse:</b> Inputs shift to $0111_2$ ($7_{10}$) and $1110_2$ ($14_{10}$), yielding $21_{10}$[cite: 59, 63]. The carry output goes high, and the display reflects the modulo value ($21 - 16 = 5$)[cite: 63].</li>
  <li><b>Fourth Pulse:</b> Inputs shift to $1111_2$ ($15_{10}$) and $1111_2$ ($15_{10}$), yielding a total sum of $30_{10}$ with an active carry probe, displaying $30 - 16 = 14$[cite: 59, 63].</li>
</ul>

<table>
  <tr>
    <td align="center" width="50%">
      <b>First Pulse (Sum = 9)</b><br>
      <img width="957" height="486" alt="image" src="https://github.com/user-attachments/assets/5c66144b-f390-4d17-8341-af41c2b88d9f" />
<br>
      <p>Right shift value = 1, Left shift value = 8, Sum = 9[cite: 57, 58, 62]</p>
    </td>
    <td align="center" width="50%">
      <b>Second Pulse (Sum = 15)</b><br>
      <img width="900" height="450" alt="image" src="https://github.com/user-attachments/assets/a877873a-9693-4c51-9bec-11bffdb6f9ee" />
<br>
      <p>Right shift value = 3, Left shift value = 12, Sum = 15[cite: 58, 62]</p>
    </td>
  </tr>
  <tr>
    <td align="center" width="50%">
      <b>Third Pulse (Sum = 21)</b><br>
      <img width="878" height="438" alt="image" src="https://github.com/user-attachments/assets/76576129-4a59-45c5-ad22-1c2b2e4ddc74" />
<br>
      <p>Right shift value = 7, Left shift value = 14, Sum = 21 (Carry high, display shows $21 - 16 = 5$)[cite: 59, 63]</p>
    </td>
    <td align="center" width="50%">
      <b>Fourth Pulse (Sum = 30)</b><br>
      <img width="951" height="489" alt="image" src="https://github.com/user-attachments/assets/bf76c3b0-da7a-4622-b1e0-73bc638b58dd" />
<br>
      <p>Right shift value = 15, Left shift value = 15, Sum = 30 (Carry high, display shows $30 - 16 = 14$)[cite: 59, 63]</p>
    </td>
  </tr>
</table>
