<h1>Shift-and-Add 4-Bit ALU</h1>

Demonstrates sequential 4-bit binary arithmetic, where multiplication is done by repeated shifting and adding.

<h2>What this project does</h2>
<li>Takes two 4-bit inputs: A and B</li>
<li>Supports these operations: [add, subtract, multiply (shift-and-add), ...] </li>
<li>Produces an [8-bit] result</li>
<li>Works one step per clock cycle (sequential), not all at once</li>
<h2>How shift-and-add works</h2>
<li>Start with the result set to 0.</li>
<li>Look at the lowest bit of B. If it is 1, add A to the result.</li>
<li>Shift A left by one place and shift B right by one place.</li>
<li>Repeat 4 times (once per bit).</li>
