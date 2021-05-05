# AUR_luxcorerender-bin
Arch Linux AUR files for luxcorerender-bin package: [see here](https://aur.archlinux.org/packages/luxcorerender-bin/)

## Status
Current status: pre alpha

| Component | Status | Notes |
| --- | --- | --- |
| LuxCoreUI | :heavy_check_mark: | |
| PyLuxCoreTools | :x: | See [PyLuxCoreTools - Segmentation Fault @ LuxCoreRender Forums](https://forums.luxcorerender.org/viewtopic.php?f=4&t=3547) |
| Scenes | :grey_question: | Properly installed, but there are issues in use, see [LuxCore Issue #525](https://github.com/LuxCoreRender/LuxCore/issues/525) |
| SDK | :x: | Not implemented yet, see roadmap |
| Various files (License etc) | :heavy_check_mark: | |

## Roadmap
### Alpha
- [x] Application Menu entries
- [x] LuxCoreUI
- [ ] Safely manage [Open Image Denoise dependancy](https://forums.luxcorerender.org/viewtopic.php?f=4&t=3533) (memo, LD_PRELOAD)

## Beta
- [ ] Split package for SDK
- [ ] PyLuxCoreTools properly packaged

### Stable
- [x] Application Menu Entries
- [ ] All dependencies managed correctly
- [ ] Example scenes working
- [x] LuxCoreUI working
- [ ] PyLuxCoreTools working
- [ ] SDK working
