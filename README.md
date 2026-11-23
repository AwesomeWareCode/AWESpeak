## **A**wesome**W**are **ESpeak**

C# binding of ESpeak that is, by C# bindings standards and by design, shitty. It is a comically direct binding of ESpeak to C#, using C#-specific features only when it makes sense, and otherwise giving you a straight path forward. Don't get an segfault using it! :)

## Usage

```c#
// Important that you call this before any ESpeak functions are called!
int sampleRate = ESpeak.Initialize(ESpeak.AudioOutput.Synchronous, 0, null, 0);
ESpeak.SetVoiceByName("en");

var samples = new List<short>();
ESpeak.SetSynthCallback((wav, events) =>
{
    samples.AddRange(wav);
    return true; // keep going
});

ESpeak.Synth("Hello, world!", out _);
ESpeak.Terminate();

// and then save the samples to a .wav file, play them through Godot, etc.
```
