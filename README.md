
Vocal Acoustic Feature & Jitter Sandbox

A small Python project where I created fake voice-like sounds from scratch and wrote simple code to measure their pitch, loudness, brightness, and shakiness.

What I Did & Why

Instead of using pre-built audio tools that hide how everything works, I built this sandbox using basic math (NumPy and SciPy) so I could see how sound analysis actually works step by step:
1. Made a grid that can capture a voice: I set up a 16,000-samples-per-second time grid. That is fast enough to capture the full range of a human voice and all of its higher overtones without missing anything.
2. Built a smooth, voice-like sound: A single pure tone sounds like a beep, not a voice. To make it sound closer to a real voice, I stacked a main pitch on top of higher harmonics, kept the pitch glides smooth so there were no clicks or glitches, and faded the start and end in and out cleanly.
3. Used a wide enough window to catch low pitches: Because a voice changes constantly, I chopped the 2-second sound into tiny 40-millisecond slices. A 40 ms slice is wide enough to fit a few full sound waves at once, which lets the code reliably find the true pitch—even for deeper voices.
4. Measured where the energy sits and how steady the pitch is:
	• Spectral Centroid: Shows the "center of gravity" of the sound's energy. A lower number means the energy sits in the deeper, calmer tones; a higher number means more energy is pushed into sharper, tenser upper tones.
	• Local Jitter: Measures tiny, rapid wobbles in pitch from one wave cycle to the next (comparing a calm voice vs. a tense/aroused voice).

What It Looks Like


What Happens If the Window Is Too Small?

I also tested shrinking the slice size from 40 ms down to 10 ms. When the slice is too short, the code loses track of deeper pitches because it can't fit enough complete sound waves inside the window to measure them accurately.
