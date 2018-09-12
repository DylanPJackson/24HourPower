// Mess with UPDATES_PER_SECOND to define how smooth/blocky the animation is
// Mess with startIndex to define how fast the animation moves
// Mess with colorIndex to define the length of each segment of the animation
// Mess with currentTime to determine how long it takes to loop through all the colors

#include <FastLED.h>
#define LED_PIN 7
#define COLOR_ORDER GRB
#define CHIPSET WS2811
#define NUM_LEDS 150
#define BRIGHTNESS 110

#define UPDATES_PER_SECOND 20
#define INTERVAL 100

boolean firstTime;
CRGB leds[NUM_LEDS];
CRGBPalette16 currentPalette;
CRGBPalette16 targetPalette;
TBlendType    currentBlending;

// The color for each hour of the day 
CRGB black;
CRGB zero;
CRGB one;
CRGB two;
CRGB three; 
CRGB four;
CRGB five;
CRGB six;
CRGB seven;
CRGB eight;
CRGB nine;
CRGB ten;
CRGB eleven;
CRGB twelve;
CRGB thirteen;
CRGB fourteen;
CRGB fifteen;
CRGB sixteen;
CRGB seventeen;
CRGB eighteen;
CRGB nineteen;
CRGB twenty;
CRGB twentyone;
CRGB twentytwo;
CRGB twentythree;

void setup() {
  delay(3000);
  FastLED.addLeds<CHIPSET, LED_PIN, COLOR_ORDER>(leds, NUM_LEDS).setCorrection( TypicalLEDStrip );
  FastLED.setBrightness(BRIGHTNESS);
  black = 0x000000;
  setHourColours();
  setCurrentPalette(black, black);
  setTargetPalette(black, zero);
  currentBlending = LINEARBLEND;
  firstTime = true;
}

void loop() {

    setupSimpleVibes();

    uint8_t maxChanges = 24;
    nblendPaletteTowardPalette( currentPalette, targetPalette, maxChanges);
    
    static uint8_t startIndex = 0;
    startIndex = startIndex + 1; /* motion speed */
    
    FillLEDsFromPaletteColors( startIndex);
    
    FastLED.show();
    FastLED.delay(1000 / UPDATES_PER_SECOND);

}

void FillLEDsFromPaletteColors( uint8_t colorIndex)
{
    uint8_t brightness = BRIGHTNESS;
    
    for( int i = 0; i < NUM_LEDS; i++) {
        leds[i] = ColorFromPalette( currentPalette, colorIndex, brightness, currentBlending);
        colorIndex += 3; /* length of segments */
    }
}

void SetupPalettetoPalette()
{
  unsigned long currentTime = (millis() / 1000) % 86400;
  // Check ensures that the first time through passes and then fades correctly for future
    if(currentTime == 82800){
    setTargetPalette(black, twentythree);
  } else if(currentTime == 79200){
    setTargetPalette(black, twentytwo);
  } else if(currentTime == 75600){
    setTargetPalette(black, twentyone);
  } else if(currentTime == 72000){
    setTargetPalette(black, twenty);
  } else if(currentTime == 68400){
    setTargetPalette(black, nineteen);
  } else if(currentTime == 64800){
    setTargetPalette(black, eighteen);
  } else if(currentTime == 61200){
    setTargetPalette(black, seventeen);
  } else if(currentTime == 57600){
    setTargetPalette(black, sixteen);
  } else if(currentTime == 54000){
    setTargetPalette(black, fifteen);
  } else if(currentTime == 50400){
    setTargetPalette(black, fourteen);
  } else if(currentTime == 46800){
    setTargetPalette(black, thirteen);
  } else if(currentTime == 43200){
    setTargetPalette(black, twelve);
  } else if(currentTime == 39600){
    setTargetPalette(black, eleven);
  } else if(currentTime == 36000){
    setTargetPalette(black, ten);
  } else if(currentTime == 32400){
    setTargetPalette(black, nine);
  } else if(currentTime == 28800){
    setTargetPalette(black, eight);
  } else if(currentTime == 25200){
    setTargetPalette(black, seven);
  } else if(currentTime == 21600){
    setTargetPalette(black, six);
  } else if(currentTime == 18000){
    setTargetPalette(black, five);
  } else if(currentTime == 14400){
    setTargetPalette(black, four);
  } else if(currentTime == 10800){
    setTargetPalette(black, three);
  } else if(currentTime == 7200){
    setTargetPalette(black, two);
  } else if(currentTime == 3600){
    setTargetPalette(black, one);
  } else if(currentTime == 0){
    setTargetPalette(black, zero);
  }
}

void setCurrentPalette(CRGB colour1, CRGB colour2){
  currentPalette = CRGBPalette16(
                                   colour1,  colour2,  colour1,  colour2,
                                   colour1,  colour2,  colour1,  colour2,
                                   colour1, colour2, colour1, colour2,
                                   colour1, colour2, colour1,  colour2 );
}

void setTargetPalette(CRGB colour1, CRGB colour2){
  targetPalette = CRGBPalette16(
                                   colour1,  colour2,  colour1,  colour2,
                                   colour1,  colour2,  colour1,  colour2,
                                   colour1, colour2, colour1, colour2,
                                   colour1, colour2, colour1,  colour2 );
}

void setHourColours(){
  zero = 0x4B0082; // midnight
  one = 0x5F1F93;
  two = 0x733EA4;
  three = 0x885DB6;
  four = 0x9C7CC7;
  five = 0xB19CD9; // morning
  six =  0x979FDE;
  seven = 0x7EA2E3;
  eight = 0x65A5E9;
  nine = 0x4BA8EE;
  ten = 0x32ABF4;
  eleven = 0x19AEF9;
  twelve = 0x00B2FF; // noon
  thirteen = 0x22A7E5;
  fourteen = 0x459DCC;
  fifteen = 0x6893B3;
  sixteen = 0x8B8899;
  seventeen = 0xAE7E80;
  eighteen = 0xD17467;
  nineteen = 0xF46A4E; // evening
  twenty = 0xD25458;
  twentyone = 0xB03F62;
  twentytwo = 0x8E2A6D;
  twentythree = 0x6C1577;
}
