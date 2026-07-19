# Gyro Zeppeli hero refresh — design specification

## Goal

Replace the generic robot in the existing GitHub profile hero with an original AI-operator interpretation of Gyro Zeppeli while preserving the approved Blacksite Operator identity.

## Scope

- Replace only `assets/gyro-blacksite.webp` and update its alt text in `README.md`.
- Keep every README section, claim, animation, badge, project description, statistic, link, and footer unchanged.
- Keep the final repository tree limited to `README.md` and `assets/gyro-blacksite.webp`.

## Character treatment

Gyro must be recognizable through his wide-brim teal hat with goggles, long blond hair, confident expression, western-inspired clothing, and one Steel Ball. He is reinterpreted as a calm AI systems operator rather than copied from a specific manga panel or anime frame.

The Steel Ball carries a restrained phosphor-green Spin signal that visually connects the character to the terminal environment. Small cyan, amber, and magenta diagnostics remain secondary accents. No horse, combat pose, weapon, franchise logo, manga lettering, generated text, or exaggerated neon is introduced.

## Composition invariants

- Preserve the 3:1 hero ratio and approximately 55 percent dark negative space on the left.
- Keep the mascot on the right third at the existing terminal workstation.
- Preserve the OLED-black room, green CRT displays, scanlines, low-key lighting, and premium hacker/AI mood.
- Keep important details away from the crop edges and make the face, hat, hair, and Steel Ball readable at GitHub README width.

## Image workflow

Use the current hero as the edit target. Use canonical character art only as a temporary identity reference and do not ship or copy that source asset. Generate one edited candidate with the built-in ImageGen tool, inspect it at original resolution, and perform one targeted iteration only if character recognition or composition fails.

The generated source remains outside the repository. Convert the accepted result to a 1600-pixel-wide WebP below 2 MB and replace the existing project asset.

## Verification

- Compare the new image against the current hero for ratio, left-side negative space, palette, and terminal continuity.
- Inspect the image at original resolution and README-width scale for malformed hands, face, hat, Steel Ball, text-like artifacts, and unintended logos.
- Render the README through GitHub's Markdown API.
- Check desktop and 390-pixel mobile layouts for loading and horizontal overflow.
- Validate the final diff contains only the WebP replacement and the hero alt-text adjustment.
- After push, confirm the live profile loads the new image through GitHub Camo.

## Ready when

The live profile retains the existing Blacksite Operator composition but the right-side mascot is clearly readable as an AI-operator version of Gyro Zeppeli, with no other README behavior or content changed.
