# Push-up Coach

A web app that watches your push-ups through your phone or laptop camera, counts only good reps, works out which push-up type you're doing, and helps you progress to harder variations.

Everything runs inside your browser. Your video never leaves your device.

**Progress: step 1 of 6 is done** (camera, skeleton and debug mode).

## Open the app

**https://dangledongler.github.io/Pushup-Progression/**

- Use **Chrome** on Android or a laptop, or **Safari** on iPhone.
- Tap **Start camera**, then tap **Allow** when the browser asks about the camera.
- The first load downloads about 20 MB (the body tracker), so use Wi-Fi if you can. After that it's faster.

## Camera setup

1. Stand your phone up on the floor, turned sideways (landscape), about 2 metres (6–7 ft) away.
2. Angle it at a **slant**: halfway between facing the top of your head and facing your side.
3. Your whole body, head to feet, must be in the picture.
4. The message at the bottom of the screen tells you if the angle needs fixing. Get into push-up position and wait for **"Camera angle looks good!"**

**Why a slant?** From the side, the camera sees your elbows and hips clearly, but your two hands overlap, so it can't tell regular, wide and diamond push-ups apart. From the front, it sees your hands clearly, but your legs hide behind your body, so it can't see sagging hips. A slant sees enough of both.

## Debug mode

Tap **Debug** (top right) to show or hide the live numbers. Tap **Copy numbers** to copy them, so you can paste them into a chat when something is detected wrong.

| Number | What it means |
|---|---|
| Person found | Whether the tracker can see a person, and how sure it is |
| Speed | How many camera frames are checked per second. 15+ is good. Under 10 can miss fast reps |
| Camera view | **Slant ✓** is what we want. **Side ✗** or **Front ✗** means move the phone |
| Left / Right elbow | 180° = arm straight, 90° = bent at a right angle |
| Hand gap | Gap between your wrists compared with your shoulders. 1.0× = shoulder width, 2.0× = twice as wide |
| Hip line | 0 = body straight. **Plus** = hips sagging. **Minus** = hips pushed up high |
| Body tilt | 0° = flat. **Plus** = head higher than feet (incline). **Minus** = feet higher (decline) |
| Body line uses | Whether your ankles are visible (best) or the app is falling back to your knees |
| Tracker | Which model is used and whether it's running on the graphics chip (GPU, faster) or main processor (CPU) |

On the camera picture:
- **Blue dots** = your left side, **orange dots** = your right side.
- **Yellow dashed line** = straight line from shoulders to feet. Your hips should sit on it.
- **Green dashed line** = the gap between your wrists.

## Build plan

1. ✅ Camera, skeleton and debug mode
2. ⬜ Rep counting (only counts when elbows reach about 90° and arms straighten again)
3. ⬜ Form warnings (hips sagging, hips too high, not low enough). Bad reps don't count
4. ⬜ Push-up type detection (regular, wide, diamond, archer left/right) plus a Knuckles switch
5. ⬜ Sets and progression ladder with unlocks
6. ⬜ Saved workout history

## Changing settings

The numbers the app uses to make decisions are all at the top of `index.html`, in the section called **SETTINGS YOU CAN TUNE**. Each line has a note explaining it. If the app runs slowly on an older phone, change `model: "full"` to `model: "lite"`.

## Troubleshooting

- **"Camera permission was blocked"**: tap the icon to the left of the web address (a lock or "aA"), allow the camera, then reload the page.
- **"Couldn't load the body tracker"**: check your internet connection and reload.
- **Skeleton jumps around or disappears**: add more light, wear fitted clothes, and avoid a busy background behind you.
- **Speed is under 10 frames/sec**: switch to the `lite` model (see Changing settings).
