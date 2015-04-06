Version 0.1

## The name of this speccy ##

No API is perfect, and so this one. To distinguish this Visualization API from others it could be referenced as `rainforce visualization api` or RVA for short.

## RVA Level 0: Visualizer and incoming data ##

Apps supporting this level receive input from stdin. That's it.

Example:
```
    $ runtests | visuapp
```
The command redirects output from some `runtests` command to some `visuapp` visualizer. It is the role of visualizer to understand if the data makes sense and represent the data.

If the data doesn't make any sense, visualizer should not exit or bail with error (unless explicitly requested). The common flag name for it may be added to higher API levels.

**Note**: Visualizer exit codes. Because visualizers are mostly interactive and may continue to run after the input stopped pumping in, return codes may not make sense. It may be possible to add return to future specification if the need arises (to detect if all input is parsed, if there are errors in algorithm etc.). Ideally `visuapp` could also forward non-zero return codes from the process it is connected to through the pipe, but I doubt that's possible. In any case, if you need the code, use the range from 220 to 229 (v is letter no.22 in English alphabet) as a generic error that is specific to visualization API (like if your viz requires a strict set of data and you decide to fail, but try not to fail if possible - try to handle input gracefully at first and fail only if there is nothing valuable inside at the end of stream).