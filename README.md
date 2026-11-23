> **Educational project, not for clinical use.** TrocarLab is not a medical
> device. It must never control a real robot in contact with a patient. The
> code provides no driver for a real robot.

# TrocarLab

TrocarLab is an open-source sandbox that simulates a laparoscopic surgery
robot: remote center of motion (RCM) control, safety zones, teleoperation and
a web console. It is meant to start with a single Docker command on any
computer, without a graphics card, and to come with step-by-step tutorials.

In laparoscopic surgery, the instrument enters the abdomen through a trocar
placed in a small incision. It must pivot around this point without ever
moving it. This fixed point is the RCM.

## Project status

The project is at milestone J1, the first of seven. Nothing can be run yet:
there is no code and no Docker image. The first release, v0.1.0, is planned
at the end of milestone J2.

## Contributing now

Install [pre-commit](https://pre-commit.com), then:

```sh
git clone https://github.com/itsdocafro/trocarlab.git
cd trocarlab
pre-commit install
```

Run `pre-commit install` again after each clone: it installs the Git hook in
your local `.git/` folder, which a clone does not copy.

Each change goes through a pull request whose description follows the
[pull request template](.github/PULL_REQUEST_TEMPLATE.md). If you use AI, read
[AI_POLICY.md](AI_POLICY.md).

## Versions

| Component | Version |
| --- | --- |
| ROS 2 | Jazzy (LTS, supported until May 2029) |
| MoveIt | MoveIt 2; the exact version is not frozen yet |

## Related work

TrocarLab does not invent RCM control. It aims to be a stepping stone towards
this research:

- **Open-source research platform for autonomous laparoscopic surgery**: RCM
  control, close to TrocarLab's scope. A. Rodriguez et al., "An Open-Source
  Robotics Research Platform for Autonomous Laparoscopic Surgery",
  [arXiv:2603.08490](https://arxiv.org/abs/2603.08490), 2026.
- **[dVRK](https://dvrk.readthedocs.io/)** (da Vinci Research Kit): the
  research standard for the da Vinci. P. Kazanzides et al., "An Open-Source
  Research Kit for the da Vinci Surgical System", ICRA 2014.
- **[SurRoL](https://github.com/med-air/SurRoL)**: reinforcement learning
  environments. J. Xu et al., "SurRoL: An Open-source Reinforcement Learning
  Centered and dVRK Compatible Platform for Surgical Robot Learning", IROS
  2021.
- **[AMBF](https://github.com/WPI-AIM/ambf)** (Asynchronous Multi-Body
  Framework): rich multi-body simulation. A. Munawar et al., "A Real-Time
  Dynamic Simulator and an Associated Front-End Representation Format for
  Simulating Complex Robots and Environments", IROS 2019.
- **[ORBIT-Surgical](https://orbit-surgical.github.io/)**: photorealistic
  simulation. Q. Yu et al., "ORBIT-Surgical: An Open-Simulation Framework for
  Learning Surgical Augmented Dexterity", ICRA 2024.
- **[PolygonMeshVirtualFixture](https://github.com/mli0603/PolygonMeshVirtualFixture)**:
  safety zones on a mesh. Z. Li et al., "Anatomical Mesh-Based Virtual
  Fixtures for Surgical Robots", IROS 2020. Its repository has no licence:
  TrocarLab only reads it to understand the approach and copies no code.

## Documentation

- [Specification](docs/quality/specification.md) (in French, frozen at
  v1.15): requirements, risks, architecture and milestones.
- [AI_POLICY.md](AI_POLICY.md): how AI is used in this project.
- [CLAUDE.md](CLAUDE.md): context and rules for the AI agent.
- [Pull request template](.github/PULL_REQUEST_TEMPLATE.md).
- [docs/adr/](docs/adr/): architecture decision records.
- [docs/design/](docs/design/): console wireframes and component names.

## Licence

TrocarLab is released under the Apache License 2.0: see [LICENSE](LICENSE)
and [NOTICE](NOTICE). It is provided without warranty (section 7 of the
licence).
