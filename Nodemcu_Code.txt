#include <ESP8266WiFi.h>
#include <ESP8266HTTPClient.h>
#include <ArduinoJson.h>

#include <SoftwareSerial.h>

SoftwareSerial mySerial(13, 15); // RX, TX

#define LED     D0        // Led in NodeMCU at pin GPIO16 (D0).
#define READ     D1        // Led in NodeMCU at pin GPIO16 (D0).

// WiFi Parameters
const char* ssid = "PTCL-BB";
const char* password = "90167b7e";

const char * path1;
const char * path2;

int incomingByte=0;

StaticJsonBuffer<300> JSONBuffer;

void setup() {
  Serial.begin(9600);
  mySerial.begin(9600);
  pinMode(LED, OUTPUT);   // LED pin as output.  
  pinMode(READ, INPUT);   // LED pin as output. 

  WiFi.begin(ssid, password);
    mySerial.write("Started");
    while (WiFi.status() != WL_CONNECTED) {
    delay(1000);
    mySerial.write("Connecting...");
        if (WiFi.status() == WL_CONNECTED) {
            mySerial.write("GOt Connected");
     }
  }
}



void loop() {
  
  // Check WiFi Status
  if (WiFi.status() == WL_CONNECTED) {
    //Serial.println("GOt Connected");
    
    // put your main code here, to run repeatedly:
   int buttonState = digitalRead(READ);

   // if (mySerial.available() > 0) {
            if(digitalRead(buttonState==1)){
  
                  digitalWrite(LED, HIGH);          // turn the LED on.
                // read the incoming byte:
                
                incomingByte=Serial.println(mySerial.read());
                mySerial.write("Recieved value\n");
                //mySerial.write(mySerial.read());
  
                // say what you got:
                Serial.print("Nodemcu received: ");
                Serial.println(incomingByte, DEC);
                

               // if (incomingByte==1) {
               
                  Serial.println("pressed one, so first path requested");
                  mySerial.write("pressed one, so first path requested\n");
                  HTTPClient http;  //Object of class HTTPClient
                  // http.begin("http://jsonplaceholder.typicode.com/users/1");
                  Serial.println("Trying to connect with Server");
                  http.begin("http://192.168.1.4:9090/new");
                  Serial.println("Connected with Server");
                  mySerial.write("connected with Server\n");
                  int httpCode = http.GET();
                  //Check the returning code

                  if (httpCode > 0) {
                      // Get the request response payload
                      String payload = http.getString();
                      Serial.println(payload);
                      JsonObject&  parsed= JSONBuffer.parseObject(payload);
                      path1 = parsed["Path1"];
                     Serial.println(path1);
                     mySerial.write(" First path is \n");
                     mySerial.println(path1);
                     //Clear json buffer else it will not parse data again becoz buffer will befull then
                     JSONBuffer.clear();
                    }
                    http.end();   //Close connection
                    delay(2000);
                    }
  
  

                //else if(incomingByte==50){
                else if(digitalRead(buttonState==0)){
                  digitalWrite(LED, LOW);          // turn the LED on.
                  Serial.println("pressed two second path requested\n");
                  mySerial.write("pressed two, so second path requested\n");
                  HTTPClient http;  //Object of class HTTPClient
                  // http.begin("http://jsonplaceholder.typicode.com/users/1");
                  Serial.println("Trying to connect with Server");
                  http.begin("http://192.168.1.40:9090/new");
                  Serial.println("Connected with Server");
                  mySerial.write("Connected with Server\n");
                  int httpCode = http.GET();
                  //Check the returning code

                  if (httpCode > 0) {
                      // Get the request response payload
                      String payload = http.getString();
                      Serial.println(payload);
                      mySerial.write(" Second path is \n");
                      JsonObject&  parsed= JSONBuffer.parseObject(payload);
                      path2 = parsed["Path2"];
                      Serial.println(path2);
                     mySerial.println(path2);
                     JSONBuffer.clear();
                    
                    }
                    http.end();   //Close connection
                  }

                  else{
                     Serial.println("Please Press one or two");
                     mySerial.write("Please Press one or two");
                    }
                
        //}
                                                                      
      
      // TODO: Parsing
    }
    
    //http.end();   //Close connection
  
  // Delay
   delay(2000);
}

----------------------------------------------------------------------------------------------------------------



from bottle import run, route

@route('/')
def index():
    return {"name" : "jsonDATA", "myList" : [101.11,202.788,3.89,4.3443,5.7643]}

@route('/docs')
def docss():
    return {"name" : "Ali", "myList" : [101.11]}

@route('/new')
def docss(): 
    return {"Path1":"0.1,0.2,0.3,0.4,0.5,0.6,0.7,0.8,0.9,1.0,1.1,1.2,1.3,1.4,1.5,1.6","Path2":"1111.111,3346.938,7221.061,3346.932,7221.061,3346.926,7221.054,3346.921,7221.054,3346.914,7221.054,3346.914,7221.054,3346.908,7221.048,3346.902,7221.048,3346.896,7221.048,3346.891,7221.048,3346.884,7221.048,3346.878,7221.048,3346.872,7221.054,3346.866,7221.054,3346.861,7221.054,3346.854,7221.054,3346.854,7221.054,3346.848,7221.061,3346.848,7221.061,3346.842,7221.066"}
 

run(host='0.0.0.0', port=9090, debug=True)