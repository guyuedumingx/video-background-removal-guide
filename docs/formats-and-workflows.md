# Transparent video: formats and a practical import checklist

Maintained by [Remove Background From Video](https://removebackgroundfromvideo.org/). Reviewed **25 October 2026**. Start with the file your destination can actually use.

## Which output should I choose?

| Output from this service | Transparency | Audio | Practical use |
| --- | --- | --- | --- |
| VP9 alpha WebM | Soft alpha | Supports source audio | Web/OBS destinations that decode its alpha |
| ProRes 4444 MOV | Soft alpha | Supports source audio | An editing intermediate in a compatible editor |
| GIF | Hard on/off transparency | None | Short stickers and animations where GIF is accepted |
| H.264 MP4 with a solid colour | Flattened background | Supports source audio | Normal delivery playback, or later colour keying |

A file extension is a container label. A MOV containing ProRes 422 is not interchangeable with ProRes 4444 for alpha. [Apple documents the ProRes family and alpha capabilities](https://support.apple.com/en-us/102207). The site's video-to-GIF conversion uses 12 fps and a maximum width of 480 px while preserving aspect ratio and not enlarging a smaller source. Local GIF colour key is a separate path that keeps decoded frame delays.

## How do I verify a transparent cut-out?

1. Download the original result from the [tool](https://removebackgroundfromvideo.org/#tool).
2. Put a visible light-colour image or source underneath it in the destination app.
3. Confirm that the background shows through around the subject, then repeat over a dark colour.
4. Play the whole clip, including the first and last frames. Inspect motion, hair and partial occlusion.
5. Listen for retained audio and check alignment at the beginning and end.
6. Export a short final composition and inspect that file too.

A black preview can mean a viewer displays transparency against black, or the application ignores alpha, or a conversion removed it. Test the actual file before processing again. A delivery MP4 normally flattens the finished composition.

## What should I check in my application?

| Destination | Useful check | Documentation |
| --- | --- | --- |
| OBS | Add the file as a Media Source above a visible source; check loop settings and audio | [OBS Media Sources](https://obsproject.com/kb/media-sources) |
| Premiere Pro | Put an alpha-capable MOV above another video track; inspect alpha interpretation if needed | [Adobe Interpret Footage](https://helpx.adobe.com/premiere/desktop/edit-projects/modify-clip-properties/modifying-clip-properties-with-interpret-footage.html) |
| DaVinci Resolve | Check the codec list for the OS/version; composite the cut-out above a background | [Resolve supported codecs](https://documents.blackmagicdesign.com/SupportNotes/DaVinci_Resolve_20_Supported_Codec_List.pdf) |
| CapCut | Try a short file; verify that the installed app preserves alpha, or use its own removal/keying controls | [CapCut removal guide](https://www.capcut.com/resource/how-to-remove-background-in-capcut) |

The site's [editor guide](https://removebackgroundfromvideo.org/blog/use-transparent-video-in-editors) distinguishes documented workflows from actual hands-on checks. Published checks include OBS 32.2.2 on macOS 15.3, Apple Silicon; this is not proof of every editor/version. No Premiere Pro import was tested for the published sample set.

The site's browser-based image/blur composition is currently disabled on iPhone/iPad and Safari. A server-rendered [solid-colour MP4](https://removebackgroundfromvideo.org/change-video-background) is a separate delivery option; it does not contain alpha.

## Is the output lossless?

Preserving dimensions is different from preserving every detail. Segmentation can remove fine objects, encoding can change image quality, GIF changes the palette and frame rate, and intermediate conversions may remove alpha. Choose an appropriate format and inspect representative footage.

Read the [complete format guide](https://removebackgroundfromvideo.org/blog/transparent-video-formats), [source/output tests](https://removebackgroundfromvideo.org/video-background-removal-tests) and [GIF tutorial](https://removebackgroundfromvideo.org/blog/make-transparent-gif-from-video). Return to the [main guide](../README.md).
