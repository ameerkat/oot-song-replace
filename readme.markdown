#About
This is a project dedicated to replacing the audio in ocarina of time similar
to how the retexture project's have replaced the textures with higher resolution
ones. For information on how the plugin works see [link](todo_put_link_here)
Plugin source is not hosted on github because it is not my own, I simply modified
it, it is available from the links below. Note that it was only modified to work
with ABI2 games but it shouldn't be that hard to modify the source to work with
others as long as it is HLE.

[Plugin Source](http://www.ammeerayoub.com/n64/AziAudioSrc0551w_sound_replacement.zip)
[Plugin Binary (.dll)](http://www.ammeerayoub.com/n64/AziSndReplace.dll)

#Demo Video
http://www.youtube.com/watch?v=o_vt4kEvils

#Folder Placement
The music and lists are loaded based on a hash of the rom header (first 40bytes)
ocarina of time is `b5bc0385152e9afb8f6f79aab04abfec` so place this folder in
`${emulator_dir}/plugin/hires_audio` e.g. the lists go in
`${emulator_dir}/plugin/hires_audio/b5bc0385152e9afb8f6f79aab04abfec` and the mp3s
go in `${emulator_dir}/plugin/hires_audio/b5bc0385152e9afb8f6f79aab04abfec/music/`
this project itself should be the `hires_audio` folder.

#ZREO Music
The music is not included here, go to http://www.zreomusic.com/z5 and place the mp3s
into the music subfolder

#File Format
There are 4 files as of currently that control when songs and sounds get played
when certain adpcm table load sequences occur.
##blacklist
blacklist is the list of all sounds that are blocked, currently everything is 
blocked anyway unless specified but this will be allowed to be changed in the future,
this is useful for debugging though since blocked sounds get marked as blocked in the log
rather than unknown, so you can identify new sounds.
##whitelist
whitelist is the list of sounds that are allowed to be played at all times, e.g.
in ocarina of time the ocarina is allowed.
##blocklist
blocklist is the list of sound/filename pairs, that allow you to block certain sounds
while certain songs are playing that would otherwise be whitelisted. An example is 
blocking the ocarina in the title screen.
##songlist
songlist is the list of adpcm table hash sequences and file names, currently there are 6 hashes
to a signature, this must always be the case otherwise it will be loaded incorrectly, you can
change this from the source code (SIGNATURE_BLOCK_SIZE) as long as the file matches up.
