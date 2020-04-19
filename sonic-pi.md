# Install

## Mac

```sh
$ brew cask install sonic-pi
==> Downloading https://sonic-pi.net/files/releases/v3.2.0/sonic-pi-for-mac-v3.2.0.zip
######################################################################## 100.0%
==> Verifying SHA-256 checksum for Cask 'sonic-pi'.
==> Installing Cask sonic-pi
==> Moving App 'Sonic Pi.app' to '/Applications/Sonic Pi.app'.
🍺  sonic-pi was successfully installed!
```

# About: Install
- Homepage: [Sonic Pi - The Live Coding Music Synth for Everyone](http://sonic-pi.net/)
- [Artikel dazu](https://sonicpi.weebly.com/uploads/4/4/1/2/44127859/live_coding_in_der_bildung.pdf)
- 🥁 [Sonic Pi Essentials](https://magpi.raspberrypi.org/books/essentials-sonic-pi-v1) – Buch von Sam Aaron
- [Wikipedia](https://de.wikipedia.org/wiki/Physarum_polycephalum?wprov=sfti1)
- Mac App Store: [Install Sonic Pi on Mac OSX](http://macappstore.org/sonic-pi/) (das ist nicht der AppStore!)
- [Brew Formula](https://formulae.brew.sh/cask/sonic-pi) <- genommen

# Fundsachen
- [The live coding language that lets you be an actual rock star](https://stackoverflow.blog/2020/01/29/the-live-coding-language-that-lets-you-be-an-actual-rock-star/) – stackoverflow blog
- [sonic-pi Repo](https://github.com/samaaron/sonic-pi)
  - [Tutorial (im Repo)](https://github.com/samaaron/sonic-pi/tree/master/etc/doc/tutorial)
  - 🥁 [Tutorial](https://sonic-pi.net/tutorial.html) auf sonic-pi.net (nicht gechekt, ob das das gleiche ist...)
- [Programming as Performance | Sam Aaron | TEDxNewcastle](https://www.youtube.com/watch?v=TK1mBqKvIyU) – inspirierend, aber leider ohne den Code
- [Remixing Hotel California with Sonic Pi](https://www.maxwellantonucci.com/2019/10/30/sonic-pi-hotel-california.html) – entspricht aber nicht den Erwartungen
  - [Sam Aaron live coding an ambient electro set w/ Sonic Pi](https://www.youtube.com/watch?v=G1m0aX9Lpts&feature=emb_title) – verwendet leider private samples
  - [Questions from Sam’s Jun 27th practice session](https://in-thread.sonic-pi.net/t/questions-from-sams-jun-27th-practice-session/1254)
  - [source code dazu](https://github.com/maxx1128/Sonic-Pi-Songs/blob/master/hotel_california.rb)
- Forenfragen
  - [Understanding live_loops](https://in-thread.sonic-pi.net/t/understanding-live-loops/1616) (Forumfrage)
  - [Stopping a live_loop or a thread via OSC command](https://in-thread.sonic-pi.net/t/stopping-a-live-loop-or-a-thread-via-osc-command/672)

## Code from comments to TEDx session

noch nicht ausprobiert...

### No. 1
```rb
notes = (scale :e3, :minor_pentatonic)

live_loop :foo do
  sample :loop_industrial, beat_stretch: 1, rate: 1
  sleep 1
end


live_loop :beats do
  sample :bd_haus, amp: 0
  sleep 0.5
end

live_loop :vortex do
  use_synth :tb303
  play notes.choose, release: 0.1, cutoff: 100
  sleep 0.125
end
```

### Rerezzed

```rb
use_debug false
notes = (scale :e1, :minor_pentatonic, num_octaves: 2).shuffle

live_loop :rerezzed do
  tick_reset
  t = 0.04
  sleep -t
  with_fx :bitcrusher do
    s = synth :dsaw, note: :e3, sustain: 8, note_slide: t, release: 0
    64.times do
      sleep 0.125
      control s, note: notes.tick
    end
  end
  sleep t
end

live_loop :industry do
  sample :loop_industrial, beat_stretch: 1
  sleep 1
end

live_loop :drive do
  sample :bd_haus, amp: 3
  sleep 0.5
end
```
