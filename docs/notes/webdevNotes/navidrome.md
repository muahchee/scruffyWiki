Navidrome [Uberspace]
========================
## Config options

[https://www.navidrome.org/docs/usage/configuration-options/](https://www.navidrome.org/docs/usage/configuration-options/)

---

## problem: configs are only selectively applied

`config.toml`
```
MusicFolder = '/home/user/music/'
LastFM.Enabled = false
ListenBrainz.Enabled = false
Deezer.Enabled = false
EnableSharing = true
LogLevel = 'INFO'
```

### issue 
In the debug logs, only `MusicFolder`, `LastFM.Enabled`, `ListenBrainz.Enabled,` and `LogLevel` configs were applied. I'm trying to enable sharing.

### solution
Turns out I was running an older release of Navidrome (v 0.47.5). I followed the [Uberspace tutorial when setting it up](https://lab.uberspace.de/guide_navidrome/#installation). This version didnt have the share functionality yet.

At the time of writing this, the latest release if v 0.58.0.

[Check newest release here.](https://github.com/navidrome/navidrome/releases)

to update:

```
//change version names

wget https://github.com/navidrome/navidrome/releases/download/v0.58.0/navidrome_0.58.0_linux_386.tar.gz

//install path at the end
tar -xvzf navidrome_0.58.0_linux_386.tar.gz -C ~opt/navidrome

rm navidrome_0.58.0_linux_386.tar.gz

supervisorctl restart navidrome
```

---

##  CLI snippets

### to check uptime status - 
`supervisorctl status`

### to check if `.ini` file has changed - 
`supervisorctl reread`

### to update navidrome with changed `.ini` - 
`supervisorctl update`

### to check debug logs - 
`supervisorctl tail navidrome stderr`

### restart navidrome - 
`supervisorctl restart navidrome`










