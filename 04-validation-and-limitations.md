# Validation, Scope, and Limitations

[← Project overview](../README.md) · [← Spatial memory](03-spatial-memory.md)

**Project AUTO is a working research prototype, not a production-ready object-location service.** This page separates what is implemented from what has been tested and what has not yet been demonstrated to a production standard.

The statements here are based on the supplied Project AUTO documentation, including implementation notes through October 2026. They are **not** the result of a new code audit or a fresh hardware test performed for this public showcase.

## What is implemented

The provided documentation describes the following functionality in the prototype:

| Area | Documented implementation | Important qualification |
| --- | --- | --- |
| Camera-based detection | Object detections from a local camera feed | Depends on what the detector can actually see and recognise. |
| Temporary tracking | Tracking observations while objects are visible | A temporary track is not a permanent physical identity. |
| Object re-identification | Attempted association with previously seen items | Recognition can be incorrect or unresolved. |
| Event history | Recorded additions, movements, removals, and recognised returns | Events depend on observations and identity decisions. |
| Persistent memory | Local storage of identity references and event history | Persistence does not imply perfect event coverage. |
| Named regions | Manual definition of image-based scene areas | Regions depend on a stable camera view. |
| Region queries | Development-stage location, contents, and activity queries | Terminal prompts, not a polished search interface. |

## What has been verified

The documentation reports multiple rounds of automated testing covering components such as tracking, lifecycle transitions, persistent storage, recognition logic using controlled inputs, and region queries. A documented run on **2 October 2026** recorded **281 passing tests** in its prepared test environment.

Earlier project notes also report successful addition, recognition, and return scenarios using physical camera hardware. These are **historical reports**, not independent verification performed while preparing this public documentation.

The automated tests include simulated inputs and isolated databases. They are useful for validating software behaviour, but they are **not equivalent to measuring visual recognition accuracy with real objects under varied conditions**.

## What has not been established

The supplied documentation does **not** establish:

- A measured end-to-end frame-rate guarantee or production latency target.
- A calibrated, held-out recognition-accuracy figure.
- Reliable identification under every lighting condition, camera angle, occlusion, or level of clutter.
- Distinction between physically different objects that are visually identical.
- Complete live-camera validation of every newer reference-learning and region interaction.
- Deployment readiness for a larger or multi-camera environment.

Consequently, claims such as “30 FPS end-to-end,” “98% identification accuracy,” or “works in any room” would not be supported by these sources.

## Known operating boundaries

**Single fixed view.** The documented setup watches a tabletop scene from one stationary camera. Region coordinates are image-based, not a calibrated map of the physical environment.

**Partial observability.** An object behind another object, outside the frame, or missed by the detector may not be recorded correctly. Extended visual absence can be interpreted as removal even when the object remains physically present.

**Recognition uncertainty.** Different views of the same item can cause missed matches; similar-looking objects can create incorrect matches. These are active evaluation challenges, not solved guarantees.

**Event-based memory.** AUTO stores meaningful recorded transitions rather than a complete, continuous location trajectory. A missed transition can leave history incomplete.

**Development-stage experience.** The existing controls are intended for development and testing. There is no completed natural-language search interface, voice assistant, public API, or consumer-facing app in the documented scope.

**Local hardware limitations.** Camera handling, model inference, and memory operations consume local compute resources. The documents do not provide a verified minimum hardware specification or a measured capacity limit for growing object collections.

## Privacy and data handling

In the documented architecture, inference and persistent memory operate locally; the application pipeline does not call a cloud inference service. Model downloads may still require network access during initial preparation.

Local execution is a useful privacy property, but **it is not a security certification**. The prototype has no documented production authentication, multi-user permissions, or comprehensive retention controls. Camera footage and saved object references can still reveal information about a private environment. Any broader deployment would need appropriate consent, access controls, retention rules, and security review.

## How to read the project's results

The safest description of AUTO today is:

> A local prototype that integrates detection, temporary tracking, appearance-based identity recognition, and event-based spatial memory, with automated tests and some historically reported live-hardware demonstrations. Broad recognition accuracy, operational reliability, and production performance are not yet established.

This distinction is intentional. AUTO's value as an engineering project lies in integrating these components and understanding their trade-offs—not in claiming that a complex vision problem has already been solved in every situation.

[Return to the main README](../README.md).
