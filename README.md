# Cross-platform Partial Port of [5D-PGN-Recorder](https://github.com/penteract/5D-PGN-Recorder)

A partial port of 5D-PGN-Recorder which runs on Linux and Windows.

The sound playing feature is disabled because .NET Core 3.1 does not support it.

## Important notes for Linux users

This program may require root permission to access the memory of the game.

## Build

Restore dependency [FiveDChessDataInterfaceCrossplatform](https://github.com/NKID00/FiveDChessDataInterfaceCrossplatform):

```sh
$ dotnet nuget add source --username <GitHub Username> --password <GitHub Personal Access Token> --store-password-in-clear-text --name github "https://nuget.pkg.github.com/NKID00/index.json"
$ dotnet restore
```

Build:

```sh
$ dotnet build --no-restore
```

Publish as single file:

```sh
$ dotnet publish --no-build -r linux-x64 -p:PublishSingleFile=true --self-contained false -o publish
$ dotnet publish --no-build -r win-x64 -p:PublishSingleFile=true --self-contained false -o publish
```

Binaries are located in the `publish/` directory. Prebuilt artifacts can be found in [releases](https://github.com/NKID00/5DChessRecorderCrossplatform/releases) and [GitHub Actions](https://github.com/NKID00/5DChessRecorderCrossplatform/actions/new).

# 5D Chess With Multiverse Time Travel Notation Recorder

An **unofficial** program based on https://github.com/GHXX/FiveDChessDataInterface for saving notation from games of [5D Chess With Multiverse Time Travel](https://store.steampowered.com/app/1349230/5D_Chess_With_Multiverse_Time_Travel/).

## Usage
Start this program while 5D chess is running (or vice versa). After you finish a game with at least 4 moves, a file with the name `5dpgn<date>_<time>.txt` will be saved in the folder you ran the program from. This contains the move information, but doesn't always contain the name of the variant.
It will play the sound from Tick.wav when a player in a timed game has used 1/3 of their time since the start of their turn or the previous tick.
Note: The files produced contain your timezone (as an offset from UTC), so if you consider that information sensitve, remove that field or convert it to UTC (and don't forget to change the date if necessary) before sharing. It may also be possible to infer your timezone from the filename unless that is also changed.

## Disclaimer
While it should be stable for the most part, this program may still cause crashes/desyncs or other unexpected/unwanted behaviour, hence why the developers of this project cannot be held liable for any damage caused.

## Plans
Config file (name, which tags to include, sound file, how and whether to include time, always use white's perspective)
If you close the game then restart it, the recorder should record games from the second run. At the moment it doesn't
It would save a click or 2 (and make it harder to forget to start the recorder) if the recorder started the game if it's not already running.