（1） AirLuggageFeeService<br>
 AirLuggageFeeService program refer to China International Airlines's baggage billing standard. According to the user’s cabin level, it provides users with functions such as inquiries about baggage billing, the number of pieces of luggage that can be carried, and the maximum weight of each piece of luggage. Each function serves as a sevice interface, the experiment of the interface feecalculation functionality provided by the test.<br>
1. the input specifications<br>
<table>
<tr><td>parameter</td><td>parameter's type</td><td>restriction</td><td>description</td></tr>
<tr><td>airClass</td><td>int</td><td>only the number 0-3</td><td>0, 1, 2, 3, respectively, on behalf of the passenger's cabin level: first class, business class and economy class tickets and baby</td></tr>
<tr><td>area</td><td>int</td><td>0 or 1</td><td>1 respectively on behalf of the domestic and international flightsWhether</td>
<tr><td> isstudent</td><td>boolean</td><td></td><td>Is it a student ticket</td>
<tr><td>luggage</td><td>double</td><td></td><td>Total weight of luggage carried by the user</td>
<tr><td>economicfee</td><td>double</td><td></td><td>airfare</td>
</table>
2. Output specifications<br>
The output parameter that can be obtained by calling feeCalculation function interface is “luggagefee”, which is of double type. The charging formula is as follows:<br>
luggagefee = (luggage-benchmark)*economicfee*0.015,
In the above formula, “luggagefee” is the luggage fee that should be paid by the passenger. If the passenger’s luggage is within the over-limit range, “luggagefee”=0; the benchmark is the standard amount of excess luggage, and the system will determine the specific amount according to the passenger’s cabin class and identity benchmark. Specific as shown in the table.<br>
<table>
<tr><td>airClass</td><td>Benchmark</td></tr>
<tr><td>0</td><td>40</td></tr>
<tr><td>1</td><td>30</td></tr>
<tr><td>2</td><td>20</td></tr>
<tr><td>3</td><td>0</td></tr>
</table>
Note: There is another special case that is not listed in the table. when the passenger is an international passenger and a student, benchmark value is equal to 30. Assume that all students hold economy class tickets.<br>
3.Description of transformation relationship<br>
According to the function of the program, 18 metamorphic relations are designed for the program. Because the value of economicfee in the program does not affect the program executed by the metamorphic relations, the value of economicfee is fixed to 1000 in the description of the transformation relationship.<br>
<table>
<tr><td>序号</td>	<td>R</td>	<td>Rf</td></tr>
<tr><td>1. airClass=0， isStudent=F，area=0~1，</td></tr>
<tr><td>MR1</td>	<td>luggage_=luggage+1,(40<=luggage<200)</td>	<td>luggagefee_>luggagefee</td></tr>
<tr><td>MR2</td>	<td>luggage_=2*luggage,(40<=luggage<100)</td>	<td>luggagefee_>=2*luggagefee</td></tr>
<tr><td>2. airClass=1， isStudent=F，area=0~1,</td></tr>
<tr><td>MR3</td>	<td>luggage_=luggage+1(30<=luggage<200)</td>	<td>luggagefee_>luggagefee</td></tr>
<tr><td>MR4</td>	<td>luggage_=2*luggage, (30<=luggage<100)</td>	<td>luggagefee_>=2*luggagefee</td></tr>
<tr><td>3. airClass=2， isStudent=F，area=0~1，</td></tr>
<tr><td>MR5</td>	<td>luggage_=luggage+1, (20<=luggage<200)</td>	<td>luggagefee_>luggagefee</td></tr>
<tr><td>MR6</td>	<td>luggage_=2*luggage, (20<=luggage<100)</td>	<td>luggagefee_>=2*luggagefee</td></tr>
<tr><td>4. airClass=3， isStudent=F，area=0~1，</tr>
<tr><td>MR7</td>	<td>luggage_=luggage+1, (0<=luggage<200)</td>	<td>luggagefee_>luggagefee</td></tr>
<tr><td>MR8</td>	<td>luggage_=2*luggage, (0<=luggage<100)</td>	<td>luggagefee_>=2*luggagefee</td></tr>
<tr><td>5. airClass=0， isStudent=T，area=0，</tr>
<tr><td>MR9</td>	<td>luggage_=luggage+1, (40<=luggage<200)</td>	<td>luggagefee_>luggagefee</td></tr>
<tr><td>MR10</td>	<td>luggage_=2*luggage, (40<=luggage<100)</td>	<td>luggagefee_>=2*luggagefee</td></tr>
<tr><td>6. airClass=1， isStudent=T，area=0,</td></tr>
<tr><td>MR11</td>	<td>luggage_=luggage+1, (30<=luggage<200)</td>	<td>luggagefee_>luggagefee</td></tr>
<tr><td>MR12</td>	<td>luggage_=2*luggage, (30<=luggage<100)</td>	<td>luggagefee_>=2*luggagefee</td></tr>
<tr><td>7. airClass=2， isStudent=T，area=0，</td></tr>
<tr><td>MR13</td>	<td>luggage_=luggage+1, (20<=luggage<200)</td>	<td>luggagefee_>luggagefee</td></tr>
<tr><td>MR14</td>	<td>luggage_=2*luggage, (20<=luggage<100)</td>	<td>luggagefee_>=2*luggagefee</td></tr>
<tr><td>8. airClass=3， isStudent=T，area=0，</td></tr>
<tr><td>MR15</td>	<td>luggage_=luggage+1, (0<=luggage<200)</td>	<td>luggagefee_>luggagefee</td></tr>
<tr><td>MR16</td>	<td>luggage_=2*luggage, (0<=luggage<100)</td>	<td>luggagefee_>=2*luggagefee</td></tr>
<tr><td>9. airClass=0~3， isStudent=T，area=1，</td></tr>
<tr><td>MR17</td>	<td>luggage_=luggage+1, (30<=luggage<200)</td>	<td>luggagefee_>luggagefee</td></tr>
<tr><td>MR18</td>	<td>luggage_=0.5*luggage, (60<=luggage<200)</td>	<td>luggagefee<=0.5*luggagefee</td></tr>

</table>
