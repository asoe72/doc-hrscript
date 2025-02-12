# 3.8.2 Global Variables

### Description

On the other hand, global variables defined as global can always be accessed from all job programs. If a global variable is once defined, it will not be cleared even when the program cycle is reset by an end statement or an R0 \[Enter\] operation of the main program.

### Example

If a global x is executed first, a variable x will be created, and the value will be initialized to the default value of 0. Then, it will increase to 1 in the next row. If the global x is executed again in the next program cycle, it will not be defined again, and the value of 1 will be retained because the x has been defined. On the other hand, global y=10 will carry out defining and assignment so that the value of variable y will be reset to 10 when it is executed in the next program cycle.



<table>
  <thead>
    <tr>
      <th style="text-align:left"></th>
      <th style="text-align:left"></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">0001.job</td>
      <td style="text-align:left">
        <p>global x
          <br />
        </p>
        <p> in the case x=2
          <br />
        </p>        
        <p>x=x+1 # 3
          <br />
        </p>
        <p>call 107
          <br />
        </p>
        <p>print x, y # 4, 10
          <br />
        </p>
        <p>end
          <br />
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">0107.job</td>
      <td style="text-align:left">
        <p>global y=10
          <br />
        </p>
        <p>print x, y # 3, 10
          <br />
        </p>
        <p>x=x+1 # 4
          <br />
        </p>
        <p>end
          <br />
        </p>
      </td>
    </tr>
  </tbody>
</table>

Therefore, if a global variable is to be utilized as a counter for the number of program cycles, no value should be assigned along with a definition.

<table>
  <thead>
    <tr>
      <th style="text-align:left"></th>
      <th style="text-align:left"></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p>Wrong
          <br />
        </p>
        <p>Teaching
          <br />
        </p>
      </td>
      <td style="text-align:left">
        <p>global count=0
          <br />
        </p>
        <p>count=count+1
          <br />
        </p>
        <p>&#x2026;
          <br />
        </p>
        <p>end
          <br />
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p>Correct
          <br />
        </p>
        <p>Teaching
          <br />
        </p>
      </td>
      <td style="text-align:left">
        <p>global count
          <br />
        </p>
        <p>count=count+1
          <br />
        </p>
        <p>&#x2026;
          <br />
        </p>
        <p>end</p>
      </td>
    </tr>
  </tbody>
</table>

