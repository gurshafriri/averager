<img width="502" height="274" alt="image" src="https://github.com/user-attachments/assets/821e60db-267a-4eed-9ac7-2d165b8820ed" />

# Averager

A Max for Live MIDI device that generates random pitch sets whose average matches a target pitch, for computer-aided composition or live set ups. The device is inspired by the cognitive phenomenon that humans are remarkably accurate at identifying the average pitch within a series of random pitches.

## Features

### Core Functionality
- **Pitch Averaging**: Generates random pitch sets that average to a specific target pitch (MIDI note number)
- **Real-time MIDI Output**: Outputs generated pitches as MIDI notes for use in Ableton Live

### Controls

1. **Amount**: Number of pitches to output in each set
2. **Range**: Range above and below the average pitch (determines the spread of pitches)
3. **Origin average note**: Choose whether to play the average pitch at the beginning
   - **no-origin**: Skip the origin pitch
   - **w/origin**: Include the origin pitch first
4. **Playback Direction**: Control the order of pitch output
   - **Random**: Random order
   - **Down**: Descending order
   - **Up**: Ascending order
5. **BPM Controls**: 
   - **Fixed BPM**: Choose from preset values (2000ms or 500ms intervals)
   - **Custom Function**: Use a tempo envelope curve for dynamic timing
   - **Function Editor**: Draw custom BPM curves over the duration of the note sequence

### Technical Architecture

The main logic resides in the `p creation` subpatcher, which:
1. Generates a balanced list of pitches that average to the input pitch
2. Outputs them one by one based on timing parameters
3. Uses real-time interpolation through the BPM function curve for accurate temporal control

## Installation

### As Max for Live Device (.amxd)
1. Download `averager.amxd`
2. Place it in your Ableton Live User Library
3. Drag onto a MIDI track in Ableton Live

### As Standalone Max Patch (.maxpat)
1. Download `averager.maxpat`
2. Open in Max/MSP (requires Max 8 or later)
3. Can be used independently or modified for your own needs

## Usage

### Basic Workflow
1. Add Averager to a MIDI track in Ableton Live
2. Set your target average pitch (incoming MIDI note or parameter)
3. Adjust Amount and Range to control the pitch set characteristics
4. Choose playback direction and origin mode
5. Set BPM timing (fixed or use the function curve)
6. Trigger to generate and play the pitch sequence

### Using the Function Curve
The function editor allows you to create dynamic tempo envelopes:
- **X-axis**: Position through the note sequence (automatically scaled to number of notes)
- **Y-axis**: BPM at that position (range: 50-350 BPM)
- The device interpolates linearly between breakpoints
- Real-time calculation ensures accurate timing through variable BPM changes

## Technical Details

### Pitch Generation Algorithm
The device generates pitches by:
1. Creating random offsets from the target average
2. Ensuring the set balances around the average (sum of deviations = 0)
3. Constraining pitches within the specified range
4. Optional inclusion of the origin pitch (exact average)

### Timing Engine
The BPM function curve is processed in real-time using:
- Logarithmic mean calculation for linear BPM interpolation segments
- High-resolution sampling (1000x grain) for millisecond accuracy
- Self-regulating feedback loop that adapts timing based on the function curve

## Requirements

- Ableton Live 10 or later (for .amxd)
- Max for Live (included with Live Suite, or as separate add-on)
- Max/MSP 8 or later (for standalone .maxpat development)

## Files

- `averager.amxd` - Max for Live device (ready to use in Ableton)
- `averager.maxpat` - Standalone Max patch (for development/modification)

## Use Cases

- **Computer-Aided Composition**: Generate balanced pitch materials for acoustic or electronic works
- **Live Performance**: Real-time pitch generation with controllable parameters
- **Algorithmic Composition**: Create pitch sets with specific statistical properties
- **Pedagogical Tool**: Explore concepts of pitch averaging and balance in composition
- **Studio Production**: Generate MIDI content for further editing and orchestration

## License

[Add your license here]

## Author

[Add your information here]

## Acknowledgments

Built with Max/MSP and Max for Live.
