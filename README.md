# sprint3

🎮 Integrating Music and Sound Effects in LibGDX
This README outlines how to implement background music and sound effects in a Java-based game using the LibGDX framework. Audio enhances gameplay immersion and player experience, and LibGDX makes it easy to manage sound assets efficiently.

📦 Requirements
Java Development Kit (JDK) 8 or later

LibGDX (1.11.x or compatible)

Audio files in .mp3, .ogg, or .wav format

🧱 Project Structure
Ensure you place your audio files in the android/assets/ directory, which is shared across platforms:

markdown
Copy
Edit
core/
└── src/
    └── ... (your game logic)

android/
└── assets/
    ├── music.mp3
    └── click.wav
🔊 Loading and Playing Audio
1. Music (Background Music)
Use Music for long, looping audio like background tracks.

java
Copy
Edit
import com.badlogic.gdx.audio.Music;
import com.badlogic.gdx.Gdx;

public class AudioManager {
    private Music backgroundMusic;

    public AudioManager() {
        backgroundMusic = Gdx.audio.newMusic(Gdx.files.internal("music.mp3"));
        backgroundMusic.setLooping(true);
        backgroundMusic.setVolume(0.5f); // Volume range is 0.0 to 1.0
        backgroundMusic.play();
    }

    public void dispose() {
        backgroundMusic.dispose();
    }
}
2. Sound (Short Sound Effects)
Use Sound for quick effects like button clicks or explosions.

java
Copy
Edit
import com.badlogic.gdx.audio.Sound;

public class SoundFXManager {
    private Sound clickSound;

    public SoundFXManager() {
        clickSound = Gdx.audio.newSound(Gdx.files.internal("click.wav"));
    }

    public void playClick() {
        clickSound.play(1.0f); // Volume range is 0.0 to 1.0
    }

    public void dispose() {
        clickSound.dispose();
    }
}
💡 Tips
Always call .dispose() on your Sound and Music objects when no longer needed.

You can adjust pitch and pan with Sound.play(volume, pitch, pan).

Use volume sliders or settings menus to control audio preferences in-game.

🧪 Example Usage
java
Copy
Edit
AudioManager audioManager = new AudioManager();
SoundFXManager fxManager = new SoundFXManager();

// Play a sound on event
fxManager.playClick();
📚 References
LibGDX Audio Docs

LibGDX GitHub
