stereo-cipher
=============

This composition is a sonic representation of secret sharing scheme that uses the property of interference in waves and the stereophonic perception of the human auditory system. In this cryptographic scheme, a secret message is embedded into two audio streams which are generated by mapping an alphanumeric string such as a RSA public key to a series of tones.

If we are given two harmonic sound waves with the same amplitude and frequency but one is phase shifted by 180 degrees and we superimpose them on top of each other, they will completely destroy each other. On the other hand if we superimpose two waves that are 0 degrees phase shifted, the resulting wave will have an amplitude which is twice the original one.

To decrypt the message, one plays the audio through two channels on a stereo system which will reveal the encoded secret.

#### Implementation

Let:
S be a message which is a binary string
L is the length of the embedded message which represents how many bits are in S
T a parameter which represents how many seconds of sound are used per secret bit such that T x L is the time needed to decrypt the message. In this max patch, T is regulated by a metronome.
B, the cover sound which is generated from the public key

To generate share 1 (s1):
1. Initialize s1 to B
2. For every T seconds of data, flip a coin c.
3. If c is 1, multiply s1 by -1 implying a 180 degree phase shift. Otherwise do nothing.

To generate share 2 (s2):
1. Initialize s2 to B
2. For every T seconds of data, flip a coin c.
3. Compute c' = ~(c XOR S_t) where S_t is the bit of the secret message at timestep t
4. If c' is 1, multiply s2 by -1, otherwise do nothing. 

#### License
![Creative Commons License](http://i.creativecommons.org/l/by-sa/3.0/88x31.png)

This work by Tony Chen is licensed under a [Creative Commons Attribution-ShareAlike 3.0 Unported License](http://creativecommons.org/licenses/by-sa/3.0/deed.en_US).
