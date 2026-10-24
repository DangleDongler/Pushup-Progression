# Push-up Coach

A web app that watches your push-ups through your phone's camera, counts only good reps, works out which push-up type you're doing, and moves you up a ladder of harder variations.

Everything runs inside your browser. Your video never leaves your device.

**Version 1 is complete:** camera and skeleton, rep counting, form warnings, push-up type detection, sets and progression ladder, and saved history.

## Open the app

**https://dangledongler.github.io/Pushup-Progression/**

- Use **Chrome** on Android or a laptop, or **Safari** on iPhone.
- Tap **Start camera**, then tap **Allow** when the browser asks about the camera.
- The first load downloads about 20 MB (the body tracker), so use Wi-Fi if you can.

## Camera setup (front view)

1. Stand your phone **upright** on the floor, about a forearm's length in front of where your hands will go, with the **screen facing you**.
2. Lean it against something (a shoe, a water bottle) or use a phone stand.
3. Both hands, both arms and your shoulders must be on screen. Your head being cut off at the top is fine.

Because the screen faces you, you can watch your count while you do push-ups. The app also says each count out loud (tap **Voice** to turn that off).

## How a rep is counted

1. Start at the top with your **arms straight**.
2. Go down until your elbows are bent to **about 90°**, or your shoulders have come down at least 55% of the way to your hands.
3. Come back up until your **arms are straight** again.

Half reps don't count. You'll see and hear "Go lower".

## Sets and the ladder

- A **set** starts with your first rep. It finishes when you tap **Finish set**, when you get out of push-up position for 4 seconds, or when 20 seconds pass without a rep.
- After each set you'll see how many good reps you did, which types, and your progress toward the next level.
- Sets less than an hour apart count as one **workout**.

The **Ladder** button shows the levels:

| Level | Push-up | To unlock the next level (in one workout) |
|---|---|---|
| 1 | Incline (hands on a bench, couch or low table) | 3 sets of 12 |
| 2 | Regular | 3 sets of 12 |
| 3 | Diamond | 3 sets of 12 |
| 4 | Decline (feet up on a chair) | 3 sets of 10 |
| 5 | Archer | 3 sets of 8 per side |
| 6 | Pseudo-planche | 3 sets of 8 |
| 7 | One-arm (the final goal) | 3 sets of 5 per side |

Everyone starts at level 1. If you can already do the earlier levels, open **Ladder** and tap **Start from here** on the right level.

## Push-up types

**Detected automatically** (with the Exercise menu on **Auto-detect**):
- **Regular**: hands a bit wider than your shoulders.
- **Wide**: hands much wider than your shoulders.
- **Diamond**: hands close together under your chest.
- **Archer**: one arm bends while the other stays straight out to the side. Left and right are counted separately.
- **Knee**: on your knees instead of your toes. Spotted when your knees sit very low on screen (resting on the floor) or are clearly bent (feet up). Knee push-ups never count toward the ladder. Whether they count at all is up to you (see Settings).

**Picked by you** in the Exercise menu, because the camera can't judge them from the front:
- **Incline** and **Decline**: the front camera can't tell how high your hands or feet are.
- **Pseudo-planche** and **One-arm**.
- **Knuckles**: tap the Knuckles button. The camera can't reliably tell fists from flat hands.

When your ladder level needs one of these, the Exercise menu switches to it automatically.

## Settings

Tap **Settings** (the gear icon on a phone):
- **Count knee push-ups**: on (the default) means knee push-ups count and show as "Knee". Off means they show "Not counted: knee push-up".

## Honest limits

- **Knee push-up detection depends on where the phone is.** From the front, your knees are mostly hidden behind your body, so the tracker partly guesses where they are. With the phone in its usual spot, 3 regular and 3 knee push-ups were all labelled correctly. In earlier tests with the phone placed a little differently, regular and knee push-ups weren't told apart. Keep the phone in the same spot each time. If a rep gets the wrong label, use Copy numbers (see Debug mode) so the cut-offs can be adjusted.

- **Hip sagging and hips too high are not checked from the front.** From the front, your hips are hidden behind your shoulders and the tracker can only guess where they are. Workaround: if you want hip checks, put the phone at a **slant** (halfway between facing your head and facing your side, about 2 m away, whole body in view). The app notices the slanted camera and turns hip checks on automatically.
- **The "wide", "diamond" and "archer" cut-off numbers are first guesses.** They were set from one test video of regular push-ups. They may need adjusting for your body and camera position (see Debug mode).
- **Slow phones:** if Speed in debug mode drops below about 8 frames per second, very fast reps can be missed. Switching to the `lite` model helps (see Changing settings).

## Debug mode

Tap **Debug** (the bug icon on a phone) to show or hide live numbers. Tap **Copy numbers** to copy them along with your last 10 reps, then paste them into a chat when something is detected wrong.

| Number | What it means |
|---|---|
| Person | Whether the tracker can see you, and how sure it is |
| Speed | Camera frames checked per second. 15+ is great, under 8 can miss fast reps |
| View | **Front ✓** or **Slant ✓** are fine. **Side ✗** means turn the phone to face your head |
| Left / Right elbow | 180° = arm straight, 90° = bent at a right angle |
| Working arm | Which arm the counter is following: both, or one (archer, one-arm) |
| Shoulder drop | How far your shoulders have come down toward your hands. 0% = top, 55%+ = deep enough |
| Hand gap | Gap between your wrists compared with your shoulders. About 1.4× was regular in testing |
| Hip line | 0 = body straight, plus = sagging, minus = hips high. Shows "(off)" from the front |
| Body tilt | 0° = flat, plus = head higher than feet |
| Knees | How far down the screen your knees are (0 = level with your shoulders, 1 = level with your hands) and how bent they are (180° = straight). Knees 0.9 or lower, or bent to 120° or less, means a knee push-up |
| State | Waiting for straight arms, at the top, or in a rep |
| Last rep | Type, whether it counted, lowest elbow angle, deepest shoulder drop and hand gap |

On the camera picture:
- **Blue dots** = your left side, **orange dots** = your right side.
- **Red dashed line** = the shoulder depth line. Get your shoulders down to it.
- **Green dashed line** = the gap between your wrists.

## Changing settings

The numbers the app uses to make decisions are at the top of `index.html`, in the section called **SETTINGS YOU CAN TUNE**. Each line has a note explaining it. If the app runs slowly on an older phone, change `model: "full"` to `model: "lite"`.

## Troubleshooting

- **"Camera permission was blocked"**: tap the icon to the left of the web address (a lock or "aA"), allow the camera, then reload the page.
- **"Couldn't load the body tracker"**: check your internet connection and reload.
- **Reps aren't counting**: turn on Debug and watch the elbow numbers. Your arms must reach 160° or more at the top. At the bottom, either the elbows need to reach 100° or less, or the shoulder drop needs to reach 55%.
- **Skeleton jumps around or disappears**: add more light, and make sure both hands and shoulders are on screen.

## Planned for later

- Locking other apps until you finish your push-ups (needs a real phone app; a website can't lock apps)
- A paid subscription
- iPhone and Android apps
