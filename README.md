import React, { useState } from "react";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Card, CardContent } from "@/components/ui/card";

const HarmonicaApp = () => {
  const [song, setSong] = useState("");
  const [artist, setArtist] = useState("");
  const [savedSongs, setSavedSongs] = useState([]);

  const handleSaveSong = () => {
    if (song && artist) {
      setSavedSongs([...savedSongs, { song, artist }]);
      setSong("");
      setArtist("");
    }
  };

  return (
    <div className="p-4 max-w-xl mx-auto">
      <h1 className="text-xl font-bold mb-4">Harmonica Song Sheet App</h1>
      <Input
        placeholder="Enter song name"
        value={song}
        onChange={(e) => setSong(e.target.value)}
        className="mb-2"
      />
      <Input
        placeholder="Enter artist name"
        value={artist}
        onChange={(e) => setArtist(e.target.value)}
        className="mb-2"
      />
      <Button onClick={handleSaveSong} className="w-full mb-4">
        Save Song
      </Button>
      <div>
        {savedSongs.map((s, index) => (
          <Card key={index} className="mb-2">
            <CardContent>
              <p className="font-semibold">{s.song}</p>
              <p className="text-sm text-gray-600">{s.artist}</p>
            </CardContent>
          </Card>
        ))}
      </div>
    </div>
  );
};

export default HarmonicaApp;
