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
$assocArray = [
    "name" => "John",
    "age" => 30,
    "email" => "john@example.com"
];
echo $assocArray["name"]; // Output: John
foreach ($assocArray as $key => $value) {
    echo "$key: $value\n";
}
#duplicate keys overwrite the first one
$deplicate_array = [true => "a" , 1 => "b" , "1" => "c" , 1.8 => "d"] ; // [1 => d ] , 1.8 overwrite all of 1 , true also 1

array_pop($array); // pop remove the last item
array_shift($array); // shift remove the first one
#shift and pop reindex the array that overwrite the manual index number 
#but remove using unset($array[2]) not make reindex the array
#casting
$x = 5;
var_dump((array) $x) ; // Array ([0] => 5)
$test =['a' => 1 , 'b' => null];
var_dump(array_key_exists("b" , $test)) ; // true 
var_dump(isset("b" , $test)) ; // false , cause value is null 
```
# PHP Spaceship Operator (`<=>`)

The **spaceship operator** (`<=>`) was introduced in **PHP 7**. It is used for **three-way comparisons**, returning an integer based on the relationship between two values.

## Syntax

```php
$result = $a <=> $b;
```

## Return Values

- Returns `-1` if `$a` is less than `$b`
- Returns `0`  if `$a` is equal to `$b`
- Returns `1`  if `$a` is greater than `$b`

## Works With

- Integers
- Floats
- Strings
- Arrays (element-wise)
- Objects like `DateTime`

## Examples

### Numeric Comparison

```php
echo 3 <=> 4; // -1
echo 4 <=> 4; // 0
echo 5 <=> 4; // 1
```

### String Comparison

```php
echo "apple" <=> "banana";   // -1
echo "banana" <=> "banana"; // 0
echo "cherry" <=> "banana"; // 1
```

### Sorting Example with `usort()`

```php
$numbers = [7, 2, 10, 4];

usort($numbers, function($a, $b) {
    return $a <=> $b;
});

print_r($numbers); // [2, 4, 7, 10]
```
