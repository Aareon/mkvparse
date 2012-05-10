Simple easy-to-use hacky matroska parser

Define your handler class:

    class MyMatroskaHandler(mkvparse.MatroskaHandler):
        def tracks_available(self):
            ...

        def segment_info_available(self):
            ...

        def frame(self, track_id, timestamp, data, more_laced_blocks, duration, keyframe_flag, invisible_flag, discardable_flag):
            ...

and `mkvparse.mkvparse(file, MyMatroskaHandler())`


Supports lacing and setting global timecode scale, subtitles (BlockGroup). Does not support cues, tags, chapters, seeking and so on. Supports resyncing when something bad is encountered in matroska stream.

Also contains example of generation of Matroska files from python

Also contains mkv2xml and xml2mkv: tools that convert Matroska files to/from XML plaintext. [Example XML file](http://vi-server.org/pub/xml2mkv_test.xml) . Example command:

    $ cat test3.mkv | ./mkv2xml | ./xml2mkv | mplayer - # convert to XML and back and play

Subtitles should remain as text, binary data gets encoded to hex.


Licence=MIT
