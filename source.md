<section id="themes">
	<h2>Themes</h2>
		<p>
			Set your presentation theme: <br>
			<!-- Hacks to swap themes after the page has loaded. Not flexible and only intended for the reveal.js demo deck. -->
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/black.css'); return false;">Black (default)</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/white.css'); return false;">White</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/league.css'); return false;">League</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/sky.css'); return false;">Sky</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/beige.css'); return false;">Beige</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/simple.css'); return false;">Simple</a> <br>
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/serif.css'); return false;">Serif</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/night.css'); return false;">Night</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/moon.css'); return false;">Moon</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/solarized.css'); return false;">Solarized</a>
		</p>
</section>

H:

# Successions 

by  [Sebastian Chaves](https://github.com/adamantwharf) - [Laura Santos](https://github.com/lsfinite) - [Jimmy Pulido](https://github.com/jiapulidoar)

H:

# Index
<!-- .slide: data-background="#7E2121" --> 
 1. Super Class <!-- .element: class="fragment" data-fragment-index="1"-->
 1. Abundant Numbers <!-- .element: class="fragment" data-fragment-index="2"-->
 1. Leyland Numbers <!-- .element: class="fragment" data-fragment-index="3"-->
 1. Composite Numbers <!-- .element: class="fragment" data-fragment-index="4"-->
 1. Representations <!-- .element: class="fragment" data-fragment-index="5"-->
 

H:
<!-- .slide: data-background="#005050" -->
# SuperClass 

 
V:
 
## What is it about?
Code of  class <!-- .element: class="fragment" data-fragment-index="1"-->
V:
## Susseccion
### Processing
```java
<!--
 import java.util.Arrays;

abstract class Sequence {
  /**
   * The sequence author
   */
  abstract String author();
  
  /**
   * The sequence description
   */
  abstract String description();
  
  /**
   * Computes the nth sequence term
   */
  abstract int compute(int n);
  
  /**
   * Returns the first n seq terms as an array.
   */
  int [] toArray(int n) {
    int[] seq = new int[n];
    for (int i=0; i<n; i++)
      seq[i] = compute(i+1);
    return seq;
  }
  
  /**
   * Returns the first n seq terms as a string.
   * Sequence may then simply be printed as: println(sequence.toString(n))
   */
  String toString(int n) {
    return Arrays.toString(toArray(n));
  }
  
  // All display functions must scale the canvas properly
  
  /**
   * Display n seq terms as you wish
   */
  abstract void display(int n);
   
  /**
   * Display n seq terms as a bar chart: https://en.wikipedia.org/wiki/Bar_chart
   * Warning: Should be implemented here in the super class!
   */
  void barChart(int n) {
    //TODO misssing implementation
  }
  
  /**
   * Display n seq terms as a line chart: https://en.wikipedia.org/wiki/Line_chart
   * Warning: Should be implemented here in the super class!
   */
  void lineChart(int n) {
    //TODO misssing implementation
  }
-->
 ```
V:
## BarChart implementation
```java
<!--
 void barChart(int n) {
      int[] arr = toArray(n);
      int count = 0;
      for(int i=0; i<n;i++)
      {
          float wid = map (arr[i], arr[0],arr[n-1],arr[0],width);
          stroke(hue,100,30);
          fill ( 255);
          rect(0,(height/n)*count,wid,height/n);
          count++;
      }  
  }
-->
 ```
V:
## LineChart implementation
```java
<!--
 void lineChart(int n) {
    float xpos=0;
    float ypos=height;
    int nth=1;
    int[] seq=  toArray(n);
    for ( int i = 0; i < n; i ++)
    {
      float xpos1=  map (nth, 0, n, 0, width);
      nth ++;
      float ypos1 = map ( seq[i], 0, seq[n-1], height, 0);
      fill ( 255);
      ellipse ( xpos1, ypos1, 6, 6);
      stroke (255);
      if ( i == 0)
        stroke(0);    
      line (xpos, ypos, xpos1, ypos1); 
      xpos=xpos1;
      ypos=ypos1;
    }
}
-->
 ```
V:
## CurveFitting implementation
```java
<!--
 void curveFitting(int n) {
    noFill();
    if ( n < 3 )
      return;
    float xpos=0;
    float ypos=height;
    int nth=1;
    int[] seq=  toArray(n);
    float x = map (nth, 0, n, 0, width);
    float y = map (seq[0], 0, seq[n-1], height , 0);
    float x1 = map (nth + 1, 0, n, 0, width);
    float y1 = map (seq[1], 0, seq[n-1], height , 0);
    float x2 = map (nth + 2, 0, n, 0, width);
    float y2 = map (seq[2], 0, seq[n-1], height , 0);
    stroke ( 255);
    curve (x,y,x,y,x1,y1,x2,y2); 
    nth ++;
    for ( int i = 1; i < n - 2; i ++)
    {
      x1 =  map (nth, 0, n, 0, width);
      y1 = map (seq[i], 0, seq[n-1], height , 0);
      x2 = map (nth + 1, 0, n, 0, width);
      y2 = map (seq[i + 1], 0, seq[n-1], height , 0);
      float x3 = map (nth + 2, 0, n, 0, width);
      float y3 = map (seq[i + 2], 0, seq[n-1], height , 0);
      nth ++;
      stroke (255);
      curve ( x,y,x1,y1,x2,y2,x3,y3);
      
      x = x1;
      y = y1;
    }
    x1 = map (nth, 0, n, 0, width);
    y1 = map (seq[n-2], 0, seq[n-1], height , 0);
    x2 = map (nth + 1, 0, n, 0, width);
    y2 = map (seq[n-1], 0, seq[n-1], height , 0);   
    stroke ( 255);
    curve ( x,y,x1,y1,x2,y2,x2,y2);
   }
-->
 ```

H:
<!-- .slide: data-background="#7E2121"  -->
# Abundant Numbers 

V:
 
 ## What is it about?
 Explanation of susseccion <!-- .element: class="fragment" data-fragment-index="1"-->

 The final code <!-- .element: class="fragment" data-fragment-index="3"--> 
V:
## Abundant Number

 What is?
  
  >In number theory, an abundant number is a number for which the sum of its proper divisors is greater than the number itself. The amount by which the sum exceeds the number is the abundance. 

   Take from [Wikipedia](https://en.wikipedia.org/wiki/Abundant_number)
V:
## Example:
12 is an abundant number. 
Divisors: 1, 2, 3, 4, 6 <!-- .element: class="fragment" data-fragment-index="1"-->

Sum: 16  <!-- .element: class="fragment" data-fragment-index="2"-->

Abundance:4  <!-- .element: class="fragment" data-fragment-index="3"-->

> 16 Is grater than 12 <!-- .element: class="fragment" data-fragment-index="4"-->


V:
## Code Processing: 
A subclass of Sequence
```java
<!-- 
class Abundant extends Sequence{
  String author()
  {
     return "No-Name"; 
  }
  String description()
  {
    return "An abundant number is a number for wich the sum of its proper divisors is grater than the number itself";
  }
  
  int sum_of_div (int n )
  {
     int cont = 0;
     for ( int i = 1 ; i < n ; i ++)
       if ( n % i == 0)
         cont += i;
     return cont;
  }
  int compute ( int n )
  {
     int cont = 0;
     int number = 0;
     while (true)
     {
       number++;
       int divisors = sum_of_div (number);
       if ( divisors > number )
       {
            cont ++;
       }
       if (cont == n)
         break;
     }
     return number;
  }
  int[] sumDivArray ( int n )
  {
    int [] div = new int[n];
    for ( int i = 0 ; i < n ; i ++ )
    {
      div[i] = sum_of_div(compute(i+1));
    }
    return div;
  }
  void display(int n)
  {
     int terms = n;
     int abundants[][] = new int[2][terms];
     abundants[0] = toArray(terms);
     abundants[1] = sumDivArray ( terms);
     float wth = 0;
    
     for (int i = 0 ; i < terms; i ++)
       wth+= abundants[1][i];
     float x=0;
     if ( n < 3 )
       wth *= 3;
     for (int i = 0 ; i < terms; i ++)
     {
       x += map (abundants[1][i]/2, 0, wth, 0, width);
     //  println (x );
       float radious =map(abundants[0][i], 0, wth, 0, width);
       fill ( hue, map ( abundants [0][i], 0, abundants[0][terms-1], 0, 100),100);
       //println ( abundants [0][i] + " 0 "  + abundants[0][terms-1] + " 0 360 MAPEO " +  map ( abundants [0][i], 0,  abundants[0][terms-1], 0, 360));
       ellipse ( x ,radious/2 + mouseY, radious, radious);
       //float y = 2 * radious + map (abundants[i][0]/2, 0, wth, 0, 1000);
       float y = radious + map(abundants[1][i]/2, 0, wth, 0, width) + mouseY;
       //ellipse ( x ,y, abundants[i][0]/2, abundants[i][0]/2);
       radious =  map(abundants[1][i], 0, wth, 0, width);
       fill ( hue + 130, map ( abundants [1][i], 0, abundants[1][terms-1], 0, 100) , 100);
       ellipse ( x ,y, radious, radious);
       x +=  map (abundants[1][i]/2, 0, wth, 0, width);
       //println (x );
     }
  }
}
-->
```





H:
# Leyland Numbers
<!-- .slide: data-background="#005050" -->

V:

## What is it about?

Explanation of Susseccion <!-- .element: class="fragment" data-fragment-index="1"-->

The final code <!-- .element: class="fragment" data-fragment-index="3"-->

V:
## Leyland numbers

What is?
>In number theory, a Leyland number is a number of the form **x^y + y^x** where x and y are integers greater than 1.
<!-- .element: class="fragment" data-fragment-index="1"-->
   

Take from [Wikipedia](https://en.wikipedia.org/wiki/Leyland_number) 

V:

## Example:


**X=2    and     Y=2**      (x,y > 1)
> X^Y + Y^X = 2^2 + 2^2 =  <!-- .element: class="fragment" data-fragment-index="1"-->
8

8 is the first leyland number  <!-- .element: class="fragment" data-fragment-index="2"-->


V:
## Code Processing: 
```java
<!-- 
class Leyland extends Sequence{
  IntList enesimo, v;

  int pow(int n, int p) //special pow 
   {
     if(p==0) return 1;
      
     else if ( p % 2 == 1 )
       return n * pow(n,p-1);
     int a = pow ( n , p/2);
     return a * a;
   }
  String author()
  {
    return "No-Name" ;
  }
  String description()
  {
    return "Numbers of the form x^y + y^x for any positive integer.";
  }
  
  int py;
  int px;
  int compute( int nu )
  {
    int n = nu;
    if ( n > 13)
      n = 13;
    v=new IntList();
    enesimo= new IntList();
    for(int i=0;i<n;i++)
      for(int j=0;j<=n - i;j++)
        {
            int m = ( pow(i+2,j+2) + pow(j+2,i+2) ); 
            if(! v.hasValue(m) )
              v.append(m);
        }
     
     v.sort();
   //  println(v);
     for(int i=0;i<nu;i++)
     {
       if ( i < v.size())
        enesimo.append(v.get(i));
       else
         enesimo.append(enesimo.get(i - 1));
   }
      return enesimo.get(nu-1);  
}
  void posy(int p)
  {
      py = p-height/2;
  }
  
  void posx(int p)
  {
      px= p-width/2;
  }
  
  void sethue(color h)
  {
     hue = h; 
  }
  
  
  
  void display(int n)
  {
    posy(mouseY);
    posx(mouseX);
    if ( n > 55 )
      n = 55;
    int lay[] = toArray(n);
    int layr[] = new int[n];
   // println( lay);
    for ( int i = 0 ; i < n ; i ++ )
      layr[n-1-i] = lay[i];
    
     
    for(int i=0;i<n;i++)
    {
      float a = map (layr[i],lay[0],layr[0],lay[0],width);
      float b = map (lay[i],lay[0],layr[0],0,100);
      fill(hue,100,b);

      //noStroke();
      stroke(hue,100,30);
      float x = width/2+  px/(a/b);
      float y = height/2+py/(a/b);
      
      if(y>height)
       y=height;
       else if(y<0)
       y=0;
      if(x>width)
        x=width;
        else if(x<0)
        x=0;
      
      ellipse(x,y,a,a);
  }
  
  }
}
-->
```




H:
# Composite Numbers
<!-- .slide: data-background="#7E2121"  -->
V:

## What is it about?

Explanation of Susseccion <!-- .element: class="fragment" data-fragment-index="1"-->

The final code <!-- .element: class="fragment" data-fragment-index="3"-->

V:
## Composite Numbers

What is?
>A composite number is a positive integer that has at least one positive divisor other than one or the number itself. In other words, a composite number is any integer greater than one that is not a prime number.
<!-- .element: class="fragment" data-fragment-index="1"-->
   

Take from [Wikipedia](https://en.wikipedia.org/wiki/Leyland_number) 



V:
## Code Processing: 
```java
<!-- 
class Composite extends Sequence {
   String author()
  {
     return "No-Name"; 
  }
  String description()
  {
    return "A composite number is a positive integer that has at least one positive divisor other than one or the number itself. In other words, a composite number is any integer greater than one that is not a prime number.";
  }
  
IntList arr;
IntList  num_div (int n ){
  arr = new IntList() ;
  for ( int i = 1; i<= n ; i ++)
  {
    if ( n % i == 0)
    arr.append (i);
  }
  return arr;
}
boolean is_comp ( int n ){
  for ( int i = 2; i < n; i ++)
    if ( n % i == 0 )
          return true;
  return false; 
}
int compute ( int n ){
  int cont = 0;
  int num = 1;
  int nth= -1;
  while (true){
    if (cont == n )
      break;
    if ( is_comp (num))
    {
      cont++;
      nth=num;
    } 
    num++;
  }
  return nth;
}

void display(int n )
{
  background (0);
  stroke (250);
  float base=0, h=0 ;
  float xpos=0, ypos = 0; 
  IntList arr = num_div (n);
  int s = arr.size();
  float column = arr.get ( (s/2) - 1);
  float row = arr.get ( s / 2 );
  if ( s%2 == 1){
    base = sqrt(width * height /n);
    h = base;
    row =  column = sqrt (n) ; 
  }
  if ( s % 2 == 0){
    base = (float )width / column;
    h=(float )height / row;
    row = arr.get ( (s/2) - 1);
    column = arr.get ( s / 2 );
   }
  int sq = 1; 
  for ( int i = 0; i < column ; i ++)
  {
    for ( int j = 0; j < row ; j ++)
    {
      fill (0);
      if ( ! is_comp(sq)){ 
         fill (280  ,50, map ( sq , 0 , n , 0 , 100));
       }
      rect ( xpos, ypos, base, h);
      //println ( xpos + "   " + ypos);
      xpos = xpos + base;
      sq++;
      //println (sq);
    }
        xpos = 0;
        ypos = ypos + h;
  }
 }
}
-->
```

H:
# Representations
<!-- .slide: data-background="#005050" -->
V:

## What is it about?
Calling classes in processing <!-- .element: class="fragment" data-fragment-index="1"-->

Running Programs in JS <!-- .element: class="fragment" data-fragment-index="2"-->

Custom representation  <!-- .element: class="fragment" data-fragment-index="3"-->

BarChart representation  <!-- .element: class="fragment" data-fragment-index="4"-->

LineChart representation <!-- .element: class="fragment" data-fragment-index="5"-->

CurveFitting representation  <!-- .element: class="fragment" data-fragment-index=6"-->


V:
## Calling Classes
In processing to change n use UP and Down arrows, to change the susseccion use LEFT and RIGHT arrows.

To change type of representration use characters 'c', 'l', 'b', 'd' in the keyboard;

```java

<!-- 
// Object declaration
Sequence sequence;
int n = 3, seq = 1 , rep = 1;
//String[] toppings = {"Cheese", "Pepperoni", "Black Olives"};
String[] nameSeq = { "Composite" , "Abundant" , "Leyland"};
color value = 0;
void setup() {
  size(700,700 );
  colorMode(HSB,360,100,100,100);
  // Object init
  
}

void mouseMoved() {
  value = (value + 1) % 360;
}

void draw() {
 // noLoop();
  background(0);
  
  
  if ( seq == 0 )
    sequence = new Composite();
  else if ( seq == 1)
    sequence = new Abundant();
  else 
    sequence = new Leyland();
  
  sequence.setHue(value);

  
  if ( rep == 1 )
    sequence.lineChart(n);
  if ( rep == 2 )
    sequence.curveFitting(n); 
   if ( rep == 3 )
     sequence.barChart(n);
   if ( rep == 4 )
    sequence.display(n);
    
    textSize(25);
  fill ( 0 ,0 ,100);
  text(nameSeq[seq] + "  n = " + n , 50, 30); 
}
void keyPressed() {
  if (key == CODED) {
    if (keyCode == UP) {
      n ++;
     
    } else if (keyCode == DOWN) {
      if ( n >=4 )
        n --;
    }
    else if ( keyCode == LEFT )
    {
      if ( seq == 0 )
        seq = 2;
      else
        seq = seq - 1 ;
    }
    else if ( keyCode == RIGHT )
    {
      seq = (seq+1) % 3;
    }
    
    clear();
  }
  if ( key == 'l' || key == 'L')
      rep = 1;
   else if ( key == 'c' || key == 'C')
      rep = 2;
   else if ( key == 'b' || key == 'B')
      rep = 3;
   else if ( key == 'd' || key == 'D')
      rep = 4;
}
-->
```

V:
## Running in java script
The next representations are running JS programs in the presentation. <!-- .element: class="fragment" data-fragment-index="1"-->

Use any key to change the succession. To change n use 'ctrl' and 'alt' keys. <!-- .element: class="fragment" data-fragment-index="2"-->

If you want to see the codes click <!-- .element: class="fragment" data-fragment-index="3"-->
 [here](https://github.com/FutureUN/PresentationSusseccionsOOP/tree/gh-pages/sketches) <!-- .element: class="fragment" data-fragment-index="3"-->
 
V:
## Custom Representation

<div id='draw_id'> </div>

V:
## BarChart Representation

<div id='barChart_id'> </div>

V:
## LineChart Representation

<div id='lineChart_id'> </div>

V:
## CurveFitting Representation

<div id='curveChart_id'> </div>

H:
THANK YOU
<figure>
    <img height='300' src='fig/tux.png' />
</figure>



