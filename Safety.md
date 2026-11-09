# Safety

Halum is for research and education. Nothing here is a medical device, and
nothing here has been clinically tested or approved. Read this before you
build, run or contribute to any Halum project.

## Do not
- Use any Halum project to diagnose, monitor or treat a person.
- Connect Halum hardware to a patient or to clinical equipment.
- Build anything that passes current into the body. Halum projects only
  measure signals, unless a project's own safety notes say otherwise.
- Describe a Halum project as medically safe, effective or approved.

## Electrodes on a person
- A computer connected to electrodes must run on battery. Unplug the charger
  and anything else that connects it to mains, such as a monitor or a powered
  USB hub. Power the board only from that computer.
- Do not take part if you have a pacemaker or other implanted electronic
  device.
- Keep EMG electrodes on one limb. Never place them across the chest.
- Do not place electrodes on broken or irritated skin. Stop if you feel
  tingling, pain or heat.
- Have someone with you when testing on a person for the first time.

## Motors and physical builds
- Moving parts can pinch. Keep fingers, hair and cables clear during tests.
- Every motor needs a way to cut power immediately.
- Each project must define what happens if the signal or software fails.
  The default is to stop moving.
- Printed hands are demonstration models. Do not fit them as a prosthesis or
  use them to bear weight or grip anything hazardous.
- Follow the manufacturer's charging and storage guidance for batteries.

## Data
- Never commit patient data or anything that could identify a person.
- Only record people who have given informed consent.
- Remove names, dates of birth and similar details before sharing recordings.
- Studies on people may need ethics approval. Check with your institution
  before you start.

## Contributing
Pull requests that change hardware, wiring, firmware or motor control must
explain the safety impact and how the change was tested.

## Reporting a safety problem
Contact [newfoundland679@gmail.com] privately, or open an issue labelled `safety`
if the problem is not sensitive. If someone is hurt, get medical help first.

## No warranty
Everything here is provided as is, and you use it at your own risk. See the
licence in each project.