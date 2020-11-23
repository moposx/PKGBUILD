 # Tips of using otf-sf-mono

Since this is the default monospaced font family of macOS and Xcode, it is possible to achieve the similar web browsing experience to macOS by parsing `SFMono-Regular` property in CSS and replace it with this font family via fontconfig.

To do so, you can add the following configuration in your fontconfig configuration file: `$XDG_CONFIG_HOME/fontconfig/fonts.conf`, typically `$HOME/.config/fontconfig/fonts.conf`:

```xml
<match target="pattern">
    <test qual="any" name="family">
        <string>SFMono-Regular</string>
    </test>
    
    <edit binding="same" mode="assign" name="family">
        <string>SF Mono</string>
    </edit>
</match>
```

After editing, you need to execute `fc-cache -fv` to update the font caches, then reopen your browsers to check if it works.
