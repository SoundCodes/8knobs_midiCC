# 8Knobs Midi Over USB

### 8knobs configured to send CC Messages


Customised for Shruti Synth controlling Cut Off, Resonance, Oscillator 1 Shape,  Oscillator 1 PWM, lfo 1 rate, Oscillator 2 Shape, Oscillator 2 parameter, Envelope 1 Release but can be used to send any custom CC value

Pot Needs to Store the Last Value and the New Value

    uint8_t old1Knob = 0;
    uint8_t new1Knob = 0;

Input Pot and bitwise Right ie making the POT value from 0 - 1023 to 1 - 127

    uint16_t oneknob = analogRead(A0);
    uint8_t new1Knob = oneknob >> 3;

Shifting and Mapping to a custom value if required to send a specific CC value other than 1 -127

    uint16_t threeknob = analogRead(A2);
    uint8_t new3Knob = threeknob >> 3;
    new3Knob = map(new3Knob, 0, 127, 0, 34);

MIDI CC output
midiEventPacket_t midiCc = { 0x0B, 0xB0, CC, potValue };

    midiEventPacket_t midiCc = { 0x0B, 0xB0, 20, new3Knob };

### Dependencies

Arduino [MidiUSB](https://www.arduino.cc/en/Reference/MIDIUSB) library
