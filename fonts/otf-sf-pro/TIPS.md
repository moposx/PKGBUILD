 # Tips of using otf-sf-pro

Since this is the system font family of macOS and iOS, it is possible to achieve the similar web browsing experience to macOS by parsing `-apple-system` and `BlinkMacSystemFont` properties in CSS and replace them with this font family via fontconfig.

To do so, you can add the following configuration in your fontconfig configuration file: `$XDG_CONFIG_HOME/fontconfig/fonts.conf`, typically `$HOME/.config/fontconfig/fonts.conf`:

(You can choose SF Pro Display or SF Pro Text or the rounded version as you like.)

```xml
<match target="pattern">
    <test qual="any" name="family">
        <string>-apple-system</string>
    </test>

    <edit binding="same" mode="assign" name="family">
        <string>SF Pro Display</string>
    </edit>
</match>

<match target="pattern">
    <test qual="any" name="family">
        <string>BlinkMacSystemFont</string>
    </test>

    <edit binding="same" mode="assign" name="family">
        string>SF Pro Display</string>
    </edit>
</match>
```

After editing, you need to execute `fc-cache -fv` to update the font caches, then reopen your browsers to check if it works.
