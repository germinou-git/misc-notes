### To fix issue where some wl-cliboard action spawn a window in the Task Manager

See this [github issue](https://github.com/bugaevc/wl-clipboard/issues/268), which has been annoying for a while, but becomes blocking when using nvim (copy is only effective after clicking on the spawned window).

[nekoalice42](https://github.com/nekoalice42)'s workaround 2 works like a charm.

1. Open System Settings > Window Management > Window Rules
2. Add new rule via a button on the right top corner
3. Description: anything you want
4. Window class (application): Choose "Regular expression" and type "wl-(copy|paste)"
5. Add Property > Focus stealing prevention
6. Focus stealing prevention: Choose "Force" and "None", if not chosen yet
7. Click "Apply"
8. Test it with wl-copy Test! and wl-paste

<img width="1970" height="590" alt="image" src="https://github.com/user-attachments/assets/c211d062-df43-4229-b9c1-85b6f913349a" />
