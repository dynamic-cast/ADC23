# Karplus-Strong Synthesis

The Karplus-Strong synthesis algorithm is a method for generating realistic plucked string instrument sounds, such as those produced by guitars, banjos, and other similar instruments. It was developed by Kevin Karplus and Alex Strong in the 1980s. By taking a noise source and subtracting frequencies to create a new tone, this algorithm is an example of subtractive synthesis.

## Subtractive Synthesis

Subtractive synthesis is a sound synthesis method that involves creating sounds by starting with complex waveforms and then subtracting or filtering out certain harmonic components to achieve the desired sound. This process typically begins with a rich and harmonically complex waveform and progressively removes or attenuates specific frequency components through various filters and signal processing techniques. The resulting sound is a simpler and more focused waveform.

Basic Overview:

* Oscillator: Subtractive synthesis often begins with an oscillator generating a harmonically rich waveform, such as a sawtooth, square, or triangle wave. These waveforms contain a wide range of harmonic frequencies.

* Filtering: Filters are a central element in subtractive synthesis. Low-pass, high-pass, band-pass, and notch filters are commonly used. A low-pass filter, for example, allows frequencies below a certain cutoff point to pass through while attenuating frequencies above that point. By adjusting the filter settings, you can shape the sound by removing or emphasizing specific frequency ranges.

* Amplitude Shaping: Envelopes are used to control the amplitude (loudness) of the sound over time. Common envelope stages include Attack, Decay, Sustain, and Release (ADSR). These stages allow you to shape how the sound evolves from the moment it's triggered until it fades out.

* Modulation: Subtractive synthesis often includes modulation sources, such as LFOs (Low-Frequency Oscillators), which can be used to modulate parameters like filter cutoff frequency, oscillator pitch, and more. Modulation adds movement and complexity to the sound.

* Effects: Additional effects like reverb, delay, chorus, and distortion can be applied to further shape and enhance the sound.

Subtractive synthesis is a flexible and widely used technique in electronic music production. It allows synthesists to create a wide variety of sounds, from rich, evolving pads to sharp, percussive leads, by sculpting the harmonic content of the initial waveform and modulating various parameters.

## Karplus-Strong: Deepdive

Below is a simplified version of the Karplus-Strong schematic.

![Karplus-Strong String Synthesis](image.png)

The diagram above highlights the main points to the Karplus-Strong synthesis model. This can be added to, with more filters and effects. Additionally, the feedback can be controlled to change the tone of the output, along with adding gain controls.

A basic overview of this algorithm:

* Initialization: Start with a buffer (array) of audio samples, which represents the sound waveform. The length of the buffer determines the fundamental frequency (pitch) of the simulated string.

* Random Noise: Fill the buffer with random noise. This noise serves as the initial excitation for the virtual string. In this example, we fill the buffer using a 1 m/s noise gate.

* Filtering: Apply a simple low-pass filter to the noise signal. The filter attenuates higher frequencies and emphasizes the fundamental frequency of the string. This filter models the dampening of high-frequency components as the string vibrates.

* Feedback Loop: Create a feedback loop by continuously processing the buffer. At each time step, you compute a new sample by averaging two previous samples and feeding them back into the buffer. This mimics the vibration of a plucked string, where energy travels back and forth along the string.

* Pitch Control: By adjusting the delay length in the feedback loop, you can control the pitch of the generated sound. Longer delays produce lower pitches, while shorter delays create higher pitches.

* Output: The generated samples from the buffer are used as the output audio signal. By continuously updating the buffer with the feedback loop, the algorithm simulates the sustained sound of a vibrating string.

The Karplus-Strong algorithm is computationally efficient and can produce convincing string-like sounds with a relatively small amount of data. It is a fundamental technique used in physical modeling synthesis for emulating the sounds of plucked string instruments.
