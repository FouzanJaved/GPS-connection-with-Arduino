#include <SoftwareSerial.h>
int m=0;

SoftwareSerial mySerial(10, 11); // RX, TX
String a;

// Defination of all values
String value1, value2, value3, value4, value5, value6,value7, value8, value9, value10, value11, value12;
String value13, value14, value15, value16, value17, value18,value19, value20, value21, value22, value23, value24;
String value25, value26, value27, value28, value29, value30,value31, value32, value33, value34, value35, value36;
String value37, value38, value39, value40, value41, value42,value43, value44, value45, value46, value47, value48;
String value49, value50, value51, value52;


//String arr[500];

#define MILES_PER_METER 0.00062137f
#define EARTH_RADIUS_METERS 6372795.0f
float flon2=1.555;
float flat2=2.567;


//Definitaion of lat and long
float lat1;
float lon1;
float lat2;
float lon2;
float lat3;
float lon3;


float lat4;
float lon4;
float lat5;
float lon5;
float lat6;
float lon6;


float lat7;
float lon7;
float lat8;
float lon8;
float lat9;
float lon9;


float lat10;
float lon10;
float lat11;
float lon11;
float lat12;
float lon12;



float lat13;
float lon13;
float lat14;
float lon14;
float lat15;
float lon15;



float lat16;
float lon16;
float lat17;
float lon17;
float lat18;
float lon18;



float lat19;
float lon19;
float lat20;
float lon20;
float lat21;
float lon21;



float lat22;
float lon22;
float lat23;
float lon23;
float lat24;
float lon24;



float lat25;
float lon25;


float gpslat;
float gpslon;

int n=0;

#define Max_index 256
char GPSIN[Max_index];
int index=0;
String latitude= "",longitude= "";
char test_char;
boolean flag=false;


const byte interruptPin=20;

void setup() {
  
  // put your setup code here, to run once:
Serial.begin(9600);
Serial1.begin(9600);
mySerial.begin(9600);
  // initialize digital pin 13 as an output.
  pinMode(13, OUTPUT);

  pinMode(interruptPin, INPUT);
  attachInterrupt(digitalPinToInterrupt(interruptPin),function1,LOW);
}

void loop() {

  digitalWrite(13, HIGH);   // turn the LED on (HIGH is the voltage level)
  
  function1();

  function2();

  calc_dist(lat1, lon1, gpslat, gpslon);
  
  calc_dist(lat2, lon2, gpslat, gpslon);

  calc_dist(lat3, lon3, gpslat, gpslon);

  calc_dist(lat4, lon4, gpslat, gpslon);

  calc_dist(lat5, lon5, gpslat, gpslon);

  calc_dist(lat6, lon6, gpslat, gpslon);

  calc_dist(lat6, lon6, gpslat, gpslon);

  calc_dist(lat6, lon6, gpslat, gpslon);

  calc_dist(lat7, lon7, gpslat, gpslon);

  calc_dist(lat8, lon8, gpslat, gpslon);

  calc_dist(lat9, lon9, gpslat, gpslon);

  calc_dist(lat10, lon10, gpslat, gpslon);

calc_dist(lat11, lon11, gpslat, gpslon);

calc_dist(lat12, lon12, gpslat, gpslon);

calc_dist(lat13, lon13, gpslat, gpslon);

calc_dist(lat14, lon14, gpslat, gpslon);

calc_dist(lat15, lon15, gpslat, gpslon);

calc_dist(lat16, lon16, gpslat, gpslon);

calc_dist(lat17, lon17, gpslat, gpslon);

calc_dist(lat18, lon18, gpslat, gpslon);

calc_dist(lat19, lon19, gpslat, gpslon);

calc_dist(lat20, lon20, gpslat, gpslon);

calc_dist(lat21, lon21, gpslat, gpslon);

calc_dist(lat22, lon22, gpslat, gpslon);

calc_dist(lat23, lon23, gpslat, gpslon);

calc_dist(lat24, lon24, gpslat, gpslon);

calc_dist(lat25, lon25, gpslat, gpslon);

}

 void function1(){
  
  // This will empty Serial register and when serial avaliable then every thing will work.:
  //Stops if serial avaliable does not works
   mySerial.flush();
   while(!mySerial.available());
  
while(mySerial.available()) {
a=mySerial.readString();
Serial.println(a);
  }

  {
//    for(int i=10; i<443; i=i+2)
//    {
//      arr[i]=a.substring(i,i+7);
//      i=i+7;
//    }

      
  //Getting first 4 values
    value1 =a.substring(10,17);
    value2= a.substring(19,26);
    value3= a.substring(28,35);
    value4= a.substring(37,44);

      //Getting second 4 values
    value5 =a.substring(46,53);
    value6= a.substring(55,62);
    value7= a.substring(64,71);
    value8= a.substring(73,80);

      //Getting third 4 values
    value9 =a.substring(82,89);
    value10= a.substring(91,98);
    value11= a.substring(100,107);
    value12= a.substring(109,116);


    //Getting third 4 values
    value13 =a.substring(118,125);
    value14= a.substring(127,134);
    value15= a.substring(136,143);
    value16= a.substring(145,152);


    //Getting third 4 values
    value17 =a.substring(154,161);
    value18= a.substring(163,170);
    value19= a.substring(172,179);
    value20= a.substring(181,188);

    //Getting third 4 values
    value21 =a.substring(190,197);
    value22= a.substring(199,206);
    value23= a.substring(208,215);
    value24= a.substring(217,224);

        //Getting third 4 values
    value25 =a.substring(190,197);
    value26= a.substring(199,206);
    value27= a.substring(208,215);
    value28= a.substring(217,224);

    //Getting third 4 values
    value29 =a.substring(226,233);
    value30= a.substring(235,242);
    value31= a.substring(244,251);
    value32= a.substring(253,260);


    //Getting third 4 values
    value33 =a.substring(262,269);
    value34= a.substring(271,278);
    value35= a.substring(280,287);
    value36= a.substring(289,296);


    
    //Getting third 4 values
    value37 =a.substring(298,305);
    value38= a.substring(307,314);
    value39= a.substring(316,323);
    value40= a.substring(325,332);


    
    //Getting third 4 values
    value41 =a.substring(334,341);
    value42= a.substring(343,350);
    value43= a.substring(352,359);
    value44= a.substring(361,368);


    
    //Getting third 4 values
    value45 =a.substring(370,377);
    value46= a.substring(379,386);
    value47= a.substring(390,396);
    value48= a.substring(398,405);

    //Getting third 4 values
    value49 =a.substring(407,414);
    value50= a.substring(416,423);
    value51= a.substring(425,432);
    value52= a.substring(435,442);







//Convertting to float
    lat1=value1.toFloat();
    lon1=value2.toFloat();
    lat2=value3.toFloat();
    lon2=value4.toFloat();

//Convertting to float
    lat3=value5.toFloat();
    lon3=value6.toFloat();
    lat4=value7.toFloat();
    lon4=value8.toFloat();


//Convertting to float
    lat5=value9.toFloat();
    lon5=value10.toFloat();
    lat6=value11.toFloat();
    lon6=value12.toFloat();


//Convertting to float
    lat7=value13.toFloat();
    lon7=value14.toFloat();
    lat8=value15.toFloat();
    lon8=value16.toFloat();


//Convertting to float
    lat9=value17.toFloat();
    lon9=value18.toFloat();
    lat10=value19.toFloat();
    lon10=value20.toFloat();


//Convertting to float
    lat11=value21.toFloat();
    lon11=value22.toFloat();
    lat12=value23.toFloat();
    lon12=value24.toFloat();

//Convertting to float
    lat13=value25.toFloat();
    lon13=value26.toFloat();
    lat14=value27.toFloat();
    lon14=value28.toFloat();

//Convertting to float
    lat15=value29.toFloat();
    lon15=value30.toFloat();
    lat16=value31.toFloat();
    lon16=value32.toFloat();

//Convertting to float
    lat17=value33.toFloat();
    lon17=value34.toFloat();
    lat18=value35.toFloat();
    lon18=value36.toFloat();


//Convertting to float
    lat19=value37.toFloat();
    lon19=value38.toFloat();
    lat20=value39.toFloat();
    lon20=value40.toFloat();


//Convertting to float
    lat21=value41.toFloat();
    lon21=value42.toFloat();
    lat22=value43.toFloat();
    lon22=value44.toFloat();


//Convertting to float
    lat23=value45.toFloat();
    lon23=value46.toFloat();
    lat24=value47.toFloat();
    lon24=value48.toFloat();

//Convertting to float
    lat25=value49.toFloat();
    lon25=value50.toFloat();

       
    Serial.println(lat1,8);
    Serial.println(lon1,8);
    Serial.println(lat2,8);
    Serial.println(lon2,8);
    
    

    delay(400);
    
  }
}  


void function2(){
  //GPS CODE
  {
      if(Serial1.available())
{ 
//  Serial.println("Data received on Serial Pin ");
  while (Serial1.available())
  { 
//    Serial.println("Data is present on Serial Pin ");
    test_char= (char)Serial1.read();
    if (test_char=='$')
    {
      Serial.println("String Received");
      index=0;
    }
    GPSIN[index]= (char)test_char;
    if (GPSIN[index]=='\n')
    {
      flag=true;
      break;
//        GPS_Process();
    }
//    delay(10);
    index++;
  }
}

if (flag==true)
//void GPS_Process()
{
//  Serial.print("Flag Executed");
//  Serial.println(GPSIN);
  if (GPSIN[0]=='$'&&GPSIN[1]=='G'&&GPSIN[2]=='P'&&GPSIN[3]=='R'&&GPSIN[4]=='M'&&GPSIN[5]=='C'&&GPSIN[6]==',')
  {
    Serial.println("GPRMC STRING RECEIVED");
    Serial.println(GPSIN);
    int comma= 0;
    for (int i=0;i<=index;i++)
    {
      if (GPSIN[i]==',')
      {
        comma++;
        if (comma==2 && GPSIN[i+1]=='A')
        { 
//          Serial.println("DATA PARTIAL VALID");
//          if (comma==12 && GPSIN[i+2]=='*')
//          {
//            Serial.println("DATA VALID");
            Serial.println("Lock Established");
            latitude= String(GPSIN[19])+String(GPSIN[20])+String(GPSIN[21])+String(GPSIN[22])+String(GPSIN[23])+String(GPSIN[24])+String(GPSIN[25])+String(GPSIN[26])+String(GPSIN[27])+String(GPSIN[28]);
            Serial.println("Latitude= "+ String(latitude)+ " - "+ String(GPSIN[30]) );
            longitude= String(GPSIN[32])+String(GPSIN[33])+String(GPSIN[34])+String(GPSIN[35])+String(GPSIN[36])+String(GPSIN[37])+String(GPSIN[38])+String(GPSIN[39])+ String(GPSIN[40])+String(GPSIN[41])+String(GPSIN[42]);
            Serial.println("longitude= "+ String(longitude)+ " - "+ String(GPSIN[44]));
//          }
        }
      }
    }
  }
  flag=false;
}
gpslat=latitude.toFloat();
gpslon=longitude.toFloat();
Serial.println(gpslat);
Serial.println(gpslon);
}

// Calculation for different points
// {
//
//  if(n==0){
//    Serial.println("1");
// calc_dist(lat1, lon1, gpslat,gpslon);
// n=n+1;
//  }
//  else if(n==1){
//    Serial.println("2");
// calc_dist(lat2, lon2, gpslat, gpslon);
// n=0;
//  }
//  
// 
//  }

  }



//digitalWrite(13, HIGH);   // turn the LED on (HIGH is the voltage level)
//delay(10000);              // wait for a second
//digitalWrite(13, LOW);    // turn the LED off by making the voltage LOW
//delay(10000);              // wait for a second






//Havershine formula
float calc_dist(float flat1, float flon1, float flat2, float flon2) {
  float dist_calc=0;
  float dist_calc2=0;
  float diflat=0;
  float diflon=0;

  //I've to spplit all the calculation in several steps. If i try to do it in a single line the arduino will explode.
    diflat=radians(flat2-flat1);
  flat1=radians(flat1);
  flat2=radians(flat2);
  diflon=radians((flon2)-(flon1));

  dist_calc = (sin(diflat/2.0)*sin(diflat/2.0));
  dist_calc2= cos(flat1);
  dist_calc2*=cos(flat2);
  dist_calc2*=sin(diflon/2.0);
  dist_calc2*=sin(diflon/2.0);
  dist_calc +=dist_calc2;

  dist_calc=(2*atan2(sqrt(dist_calc),sqrt(1.0-dist_calc)));
  float ang_calc=atan2( ((sin(diflon)) * (cos(flat2))), (cos(flat1) * sin(flat2)) - ( sin(flat1) * cos(flat2) * cos(diflon) ) );
  dist_calc*=6371000.0; //Converting to meters
  Serial.println(ang_calc);
  Serial.println("angle");
  Serial.println(dist_calc);
  Serial.println("meters");
  delay(7000);  // after every calculation 7 seond delay
  return dist_calc;
}


