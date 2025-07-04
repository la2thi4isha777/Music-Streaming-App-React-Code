import React, { useState, useRef } from 'react';

const songs = [
  { title: 'Song One', url: 'https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3' },
  { title: 'Song Two', url: 'https://www.soundhelix.com/examples/mp3/SoundHelix-Song-2.mp3' }
];

function MusicPlayer() {
  const [currentSong, setCurrentSong] = useState(0);
  const audioRef = useRef(null);

  const playSong = () => {
    audioRef.current.play();
  };

  const pauseSong = () => {
    audioRef.current.pause();
  };

  const nextSong = () => {
    setCurrentSong((currentSong + 1) % songs.length);
  };

  return (
    <div style={{ padding: '2rem' }}>
      <h2>🎵 Music Streaming App</h2>
      <h3>{songs[currentSong].title}</h3>
      <audio ref={audioRef} src={songs[currentSong].url} controls />
      <br />
      <button onClick={playSong}>Play</button>
      <button onClick={pauseSong}>Pause</button>
      <button onClick={nextSong}>Next</button>
    </div>
  );
}

export default MusicPlayer;
