# rhythmictunesimport * as Tone from 'tone';

const kick = new Tone.Player('kick.wav').toDestination(); 
const snare = new Tone.Player('snare.wav').toDestination();  
const hihat = new Tone.Player('hihat.wav').toDestination(); 
const rhythmPattern = [
  { time: '0:0', sound: kick },     
  { time: '0:2', sound: snare },    
  { time: '0:3', sound: hihat },    
  { time: '1:0', sound: kick },     
];


const loop = new Tone.Loop((time) => {
  rhythmPattern.forEach(note => {
    if (Tone.now() >= Tone.Time(note.time)) {
      note.sound.start(time);  
    }
  });
}, '1m').start(0);

Tone.start();
Tone.Transport.bpm.value = 120;  
Tone.Transport.start();
