توضیحات کد جوی استیک
#include <Servo.h> const int SW = 2; // پین دیجیتال مربوط به دکمه جوی استیک const int X = 0; // پین آنالوگ مربوط به محور X جوی استیک const int Y = 1; // پین آنالوگ مربوط به محور Y جوی استیک Servo myservo; // ایجاد یک شی از نوع سروو void setup() { myservo.attach(9); // اتصال سروو موتور به پین 9 pinMode(SW, INPUT_PULLUP); // تنظیم پین دکمه به عنوان ورودی با pull-up داخلی pinMode(Y, INPUT); // تنظیم پین محور Y به عنوان ورودی آنالوگ pinMode(X, INPUT); // تنظیم پین محور X به عنوان ورودی آنالوگ Serial.begin(9600); // شروع ارتباط سریال برای نمایش اطلاعات } void loop() { if (analogRead(Y) > 1000) { myservo.write(0); delay(1000); myservo.write(90); delay(1000); } if (analogRead(X) < 200) { myservo.write(180); delay(1000); myservo.write(0); delay(1000); } } 
#include <Servo.h>: این خط، کتابخانه سروو را فراخوانی می کند تا بتوان از توابع مربوط به کنترل سروو موتور استفاده کرد.
const int SW = 2;, const int X = 0;, const int Y = 1;: این خطوط، پین های دیجیتال و آنالوگ مورد استفاده برای جوی استیک را تعریف می کنند.
Servo myservo;: یک شیء به نام myservo از کلاس Servo ایجاد می شود.
void setup() { ... }: این تابع یک بار در ابتدای اجرای برنامه فراخوانی می شود. در اینجا:
myservo.attach(9);: سروو موتور به پین شماره 9 برد آردوینو متصل می شود.

pinMode(SW, INPUT_PULLUP); پین دیجیتال مربوط به دکمه به عنوان ورودی با pull-up داخلی تنظیم می شود. این کار باعث می شود که پین در حالت عادی HIGH باشد و هنگام فشار دادن دکمه LOW شود.
pinMode(Y, INPUT); و pinMode(X, INPUT);: پین های آنالوگ مربوط به محورهای X و Y جوی استیک به عنوان ورودی تنظیم می شوند.
Serial.begin(9600);: ارتباط سریال با سرعت 9600 بیت بر ثانیه برای نمایش اطلاعات (در صورت نیاز) فعال می شود.
void loop() { ... }: این تابع به طور مداوم اجرا می شود. در اینجا:
if (analogRead(Y) > 1000) { ... }: بررسی می شود که آیا مقدار خوانده شده از محور Y جوی استیک بیشتر از 1000 است یا خیر. اگر بیشتر باشد، سروو موتور ابتدا به زاویه 0 درجه و سپس به زاویه 90 درجه حرکت می کند و یک ثانیه در هر زاویه مکث می کند.
if (analogRead(X) < 200) { ... }: بررسی می شود که آیا مقدار خوانده شده از محور X جوی استیک کمتر از 200 است یا خیر. اگر کمتر باشد، سروو موتور ابتدا به زاویه 180 درجه و سپس به زاویه 0 درجه حرکت می کند و یک ثانیه در هر زاویه مکث می کند.
توضیح کد سرور موتور:کتابخانه Servo.h برای کنترل سروو موتور وارد برنامه شده است .
یک شیء از نوع سروو به نام myservo تعریف شده است .
در بخش setup() ، سروو موتور به پایه 9 آردوینو متصل شده است .
در حلقه loop(): - سروو موتور به ترتیب زوایای 0 ، 45 ، 90 ، 135 و 180 درجه را طی میکند . - سپس، مسیر حرکت معکوس طی شده و سروو به زاویه 0 درجه بازمیگردد . - بین هر تغییر زاویه، یک مکث 1 ثانیهای (delay(1000)) وجود دارد .
نتیجه گیری:
این پروژه نشان داد که میتوان به راحتی با استفاده از Arduino و کتابخانه Servo ، سروو موتور را در زوایای مختلف کنترل کرد . حرکت دقیق سروو موتور به زوایای مورد نظر و بازگشت به حالت اولیه، کاربرد این پروژه را در بسیاری از پروژههای رباتیک و مکانیکی به نمایش میگذارد 
توضیح کد LM:const int lm35pin = A0; // پین آنالوگ متصل به سنسور LM35 int led = 9; // پین دیجیتال متصل به LED void setup() { Serial.begin(9600); // شروع ارتباط سریال برای نمایش دما pinMode(led, OUTPUT); // تنظیم پین LED به عنوان خروجی } void loop() { int sensorValue = analogRead(lm35pin); // خواندن مقدار آنالوگ از سنسور float voltage = sensorValue * (5.0 / 1023.0); // تبدیل مقدار آنالوگ به ولتاژ float temperatureC = voltage * 100; // تبدیل ولتاژ به دما بر حسب درجه سانتیگراد Serial.print("temperature:"); // نمایش متن "temperature:" در سریال مانیتور Serial.print(temperatureC); // نمایش مقدار دما در سریال مانیتور Serial.println("*c"); // نمایش واحد سانتیگراد در سریال مانیتور if (temperatureC > 27) { // اگر دما بیشتر از 27 درجه سانتیگراد بود Serial.print("cooler on"); // نمایش متن "cooler on" در سریال مانیتور digitalWrite(led, HIGH); // روشن کردن LED } else { // در غیر این صورت digitalWrite(led, LOW); // خاموش کردن LED } delay(1000); // تاخیر 1 ثانیه } 

const int lm35pin = A0;: این خط، پین آنالوگ A0 را به عنوان پین متصل به سنسور LM35 تعریف می‌کند.

int led = 9;: این خط، پین دیجیتال 9 را به عنوان پین متصل به LED تعریف می‌کند.

Serial.begin(9600);: این خط، ارتباط سریال را با سرعت 9600 باود شروع می‌کند.

pinMode(led, OUTPUT);: این خط، پین LED را به عنوان خروجی تنظیم می‌کند.

int sensorValue = analogRead(lm35pin);: این خط، مقدار آنالوگ خوانده شده از پین سنسور را در متغیر sensorValue ذخیره می‌کند.

float voltage = sensorValue * (5.0 / 1023.0);: این خط، مقدار خوانده شده را به ولتاژ تبدیل می‌کند. برد آردوینو مقادیر آنالوگ را از 0 تا 1023 به ولتاژ تبدیل می‌کند. (1023=5V)

float temperatureC = voltage * 100;: این خط، ولتاژ را به دما بر حسب درجه سانتیگراد تبدیل می‌کند. سنسور LM35 به ازای هر 10 میلی ولت افزایش ولتاژ، 1 درجه سانتیگراد افزایش دما دارد.

Serial.print("temperature:"); و Serial.print(temperatureC); و Serial.println("*c");: این خطوط، مقدار دما را در سریال مانیتور چاپ می‌کنند.

if (temperatureC > 27) { ... } else { ... }: این ساختار شرطی، وضعیت LED را بر اساس دمای اندازه‌گیری شده کنترل می‌کند. اگر دما بیشتر از 27 درجه باشد، LED روشن می‌شود و متن “cooler on” در سریال مانیتور چاپ می شود. در غیر این صورت، LED خاموش می شود.

delay(1000);: این خط، یک ثانیه تاخیر ایجاد می‌کند تا خواندن دما به طور مداوم انجام نشود.
