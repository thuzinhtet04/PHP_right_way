**REFRENCE OPERATOR**
& is refrence operator. It doesn't assign value to variable . It assign the refrence(memory location) that mean whenever you change value of that memory location(first variable) , the second varibale auto update!.
```php
$x = 2;
$y = &$x;
$x = 3;
echo $y; //3
```

**Double Quote vs Single Qoute**
Double Quote("") can handle variable, variable auto show its value. But it not work in Single Qoute('')

**Comments**
```php
// and # can be used for single line 
/* */ for multi line
/**
* for documentation
*/
```

!comment are stop at php closing tag

**Constant in PHP**
constant can't be reassigned!
constant should be in capital letter and case sensitive,
you can control the case sensitive , but you shouldn't do it.
```php
define("APP_NAME","markdown app");
const PORT = 8000;
# constant with const are created at compile time and constant with define() are created at runtime.
# So you can't use const within control structure like loop and if statement. but define() can.
```
**Dynamic Constant**
```php
$type = "PAID";
define("STATUS_" . $type , 4); //$type make PAID for constant
echo STATUS_PAID; // 4
```
**variable variables **
it is a way to define a variable using another variable. help you to create dynamic variable.
```php
$v1 = "helo";
$$v1 = "helo2"; // $helo 
echo $$v1 , $helo , $v1 ; // helo2 , helo2 , helo
# $$v1 is not work at plain " " but work with {}**
echo "{$$v1} , $$v1 , ${$v1} " ; // helo2 , $helo , helo2
```

1.4
**You can check type with**
```php
gettype();
var_dump();
```
**Type Juggling / Type coercion**
```php
sum(int $x , int $y){
    var_dump($x , $y) // int(1) , int(2) auto overwrite type to integer
    return $x + $y;
}
sum(1,"2"); //3
// but you can reoverwrite after type juggling like this 
//  sum(int $x , int $y){ 
//     $x= 5.5 ;
//  return $x + $y } // 7.5 not switch to int , it change to float
```
But you can use the strict type mode not to happen that
```php
declare(strict_types=1) ;
sum(int $x , int $y){
    var_dump($x , $y) // int(1) , int(2) auto overwrite type to integer
    return $x + $y;
}
sum(1,"2"); // it will show error at you IDE 
// But strict mode also allow type piroty , it like integer can pass to float type 🥹
```
**Type Casting**
switch type 
```php
$x = (int)"5"; 
var_dump($x) ; // int(5)
```
**Integer**
integer can be 8digit of minus and plus
```php
$x = 5 ; // 5 base 10
$y = 0x2A; // 42 , 0x make it hexadecimal
$z = 055;// 45 , 0 predefine make it octalnumber
$a = 0b11 ; // 3 , ob make it binary number
PHP_INT_MAX ;// give you max integer of integer data type
PHP_INT_MIN ; // give you minumnm integer of integer data type
#over or lower of min or max make change data type to float
```
**Float**
```php
$x = 2.1e2 ; //210 , e mean 10 power
$y = 2.1e-2; // 0.021;
PHP_FLOAT_MAX ;
 PHP_FLOAT_MIN ; 
 #be careful using float with ceil and floor , don't compare float directly  
 #there is NAN(not a number) , INF(infinity) , you can get those when calculation 
 is_infinite($z) // return true or false , check it is infinity 
 is_finite($a) // revert of is_infinite()
 is_nan();
 floatval(5) // return float(5) , same like  $x = (float) 5;
```

1.8
**Heredoc and Nowdoc**
```php
#heredoc is support variable 
<?php
$x =3;
$test = <<<END//<-no space here
Hello $x
workd
END;
echo $test; // Hello 3
 #             world 
?>
#Nowdocs does not support variable
<?php
$x =3;
$test = <<<'END'//<-no space here
Hello $x
workd
END;
echo $test; // Hello $x
 #             world 
?>
```
**Array**
```php
$array = ['helo','workd','adads'];
echo $array[-1] ;// error happen , not like javascript
echo count($array) ;//3 , length of array
$array[] = "new"  ; // append new to $array 
print_r($array); ['helo','workd','adads','new']
```
