Download Link: https://assignmentchef.com/product/solved-lab-sheet-4-for-cs-f342-computer-architecture
<br>
<strong style="font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu, Cantarell, 'Helvetica Neue', sans-serif;"><u>Goals for the Lab</u></strong><span style="font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu, Cantarell, 'Helvetica Neue', sans-serif;">: We build up on Lab 2 and Lab 3 and explore control (conditional) statements and loops. We also explore logical operations.</span>

<strong>New Instructions: </strong>

<ol>

 <li>bne application (beq, bgtz, bltz, bgez, blez are the other conditional branch opcodes )</li>

 <li>Two groups of instructions: Branches and unconditional jump instructions.</li>

 <li>Below are the list of instructions where the branching address is within 16 bits and register values are 32 bit

  <ul>

   <li><strong>beq/ bne </strong>Branches if the quantities of two registers are equal / Not Equal.</li>

   <li><strong>bne </strong>Branches if the quantities of two registers are NOT equal.</li>

   <li><strong>bgtz / bgez / bltz / blez </strong>Branches if a quantity in a register is greater than zero / greater</li>

   <li>than or equal to zero / less than zero / less than or equal to zero.</li>

  </ul></li>

</ol>




<ol start="4">

 <li>Below are the list of instructions where the branching address is within 26 bits.

  <ul>

   <li><strong>j </strong>Jump to an address</li>

   <li><strong>jal</strong> Jump to an address, and store the return address in a register (for functions to be covered later).</li>

  </ul></li>

</ol>




<ol start="5">

 <li>Below are the list of instructions where the branching address is within 32 bits.

  <ul>

   <li><strong>jr</strong> Jump to an address stored in a register</li>

   <li><strong>jalr</strong> Jump to an address stored in a register, and store the return address in another register (for functions to be covered later).</li>

  </ul></li>

</ol>







<strong><u>Exercise 1</u></strong><strong>:</strong> Write MIPS Assembly code to find whether the input integer is even or odd.

Hint: Build up from Lab sheet 2, to read and integer into a register and then <strong><u>andi</u></strong> it with 0x1 (test for last bit as zero). Thereafter jump to report even if the result is zero.

<strong># if $a0 has the value </strong><strong>andi $a0, $a0, 1 bne $a0, $zero, </strong><strong>odd_label</strong>

<strong># print that the value is even </strong><strong>j </strong><strong>exit_label</strong> <strong>odd_label</strong><strong>: </strong>

<strong>     </strong><strong># print that the value is odd</strong> <strong>exit_label</strong><strong>:       li $v0, 10 </strong><strong># exit program </strong><strong>      syscall </strong>










<strong><u>Exercise 2</u></strong><strong>:</strong> Write MIPS Assembly code to find the length of the given string. Presently the string is coming from labelled data. Modify the code below to use <strong>j</strong> (Jump) and <strong>beq</strong> instead of <strong>bne</strong>.

<strong>.data </strong>

<strong>mystr </strong><strong>: .asciiz “This is given string” </strong>

<strong> .text </strong>

<strong>main</strong><strong>: la $a0, </strong><strong>mystr </strong><strong># find the strlen for string at this address </strong><strong>      li $v0, -1    </strong><strong># $v0 has length start at 1 because ‘ ’ counted below </strong>

<strong> </strong>

<strong>slen_0</strong><strong>: lb $t0, ($a0)    </strong><strong># load current byte, move to next </strong><strong>        addi $a0, $a0, 1 </strong>

<strong>        addi $v0, $v0, 1 </strong><strong># but first increment result </strong>

<strong>        bne $t0, $zero, </strong><strong>slen_0 </strong><strong># if current byte isn’t ‘ ’, repeat </strong>

<strong> </strong>

<strong>      move $a0, $v0          </strong><strong># display result of strlen </strong><strong>      li $v0, 1 </strong>

<strong>      syscall </strong>

<strong>      li $v0, 10 </strong><strong># exit program </strong><strong>      syscall </strong>

<strong> </strong>




<strong><u>Exercise 3</u></strong><strong>: </strong>Write MIPS Assembly code to print all the multiples of the given number between 0 and 100. Your program should allow the user to give the input number. Sample test case : Input: 25 : Output: 25 50 75

<strong>Hint:</strong> For loop implementation you can use pseudo instructions given below.

<table width="308">

 <tbody>

  <tr>

   <td width="154"><strong>Pseudoinstruction</strong></td>

   <td width="154"><strong>Translation</strong></td>

  </tr>

  <tr>

   <td width="154"><strong>bge $rt, $rs, </strong><strong>LABEL</strong></td>

   <td width="154">slt $t0, $rt, $rs beq $t0, $zero,LABEL</td>

  </tr>

  <tr>

   <td width="154"><strong>bgt $rt, $rs, LABEL</strong></td>

   <td width="154">slt $t0, $rs, $rt bne $t0, $zero,LABEL</td>

  </tr>

  <tr>

   <td width="154"><strong>ble $rt, $rs, LABEL</strong></td>

   <td width="154">slt $t0, $rs, $rt beq $t0, $zero,LABEL</td>

  </tr>

  <tr>

   <td width="154"><strong>blt $rt, $rs, LABEL</strong></td>

   <td width="154">slt $t0, $rt, $rs bne $t0, $zero,LABEL</td>

  </tr>

 </tbody>

</table>




<strong><u>Exercise 4</u></strong>: Decode (disassemble) the following instructions.

<ol>

 <li>12640007</li>

 <li>08100010</li>

 <li>08100010</li>

 <li>1d600004</li>

 <li>05400003 6. 05210002</li>

 <li>19000001</li>

</ol>