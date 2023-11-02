# Grayjay PeerTube Plugin for Libre Solutions Network

Hopefully this specific plugin will be unnecessary. 
I forked the official [peertube plugin](https://gitlab.futo.org/videostreaming/plugins/peertube) because as it currently exists, it doesn't properly load videos from remote instances.

My solution isn't very elegant, I'm not familiar with typescript, but this plugin will allow you to browse videos within the network for the [Libre Solutions Network PeerTube](https://peertube.libresolutions.network.)

## Changes made: 
- Setting the baseURL to `peertube.libresolutions.network` 
- To allow remote videos to load, i had to hardcode `getVideoPager` url parameter with: 
```url: "https://peertube.libresolutions.network"+ v.url.substring(v.url.search("/videos/")),```

    **Why?** Because when the peertube plugin loads a remote video it throws an error `No source enabled to support url` Meaning that you would need to install the peertube plug-in for *every instance* within your network. 

    Thankfully peertube seamlessly handles links to remote videos when you replace it with your instance url.

## Outstanding issues

- I would prefer to pull the baseURL parameter properly, but I had trouble making that work and decided to just hardcode it.
- I have no idea how/if this will impact casting, but hope to test that soon.
- I need to properly sign the plugin

[Plugin Documentation](https://gitlab.futo.org/videostreaming/grayjay/-/blob/master/plugin-development.md)