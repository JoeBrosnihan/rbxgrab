# RBX Grab

RBX Grab is a grab system designed to be dropped in to any experience to enable characters grabbing arbitrary objects. 

You can provide hints on how any object is intended to be held. For example, a sword can be configured so characters prefer to pick it up by its handle.

You can also hook into events to detect when objects are grabbed, released, activated, and deactivated. For example, a Script in a fire extinguisher can detect 

## API

RBX Grab communicates with other scripts through several Instances in the DataModel.

The system looks for specially named Instances that are direct children of any ancestor of the grabbed BasePart, in ascending order. First, the grabbed BasePart is checked:
1. Return a direct child with the matching Name and Class.
2. If an ObjectValue with the matching Name is present, return its Value. (Useful for directing search to an Attachment in a specific Part)
3. Check the instance's Parent, if it's not the Workspace.

A common pattern is to group several Parts into a Model and put all of the relevant grab APIs as children of the Model.

### [Attachment] GrabHint

Hints that the object is intended to be held such that the character's hand CFrame matches the GrabHint's.

### [Attachment] Aim

Hints that this objects is intended to be held such that the Attachment referenced by Aim points at a location the player is targetting.

For example, a pistol would have an Aim ObjectValue that references an Attachment aligned down the barrel so the player knows to point the pistol at the mouse.

### [BindableEvent] ActivatedEvent

Fired when the holder activates this object.

Currently, pressing the left mouse button triggers activation.

TODO: Can I switch to a BoolValue?
(Is there any problem with out of order property replication.)

### [BindableEvent] DeactivatedEvent

Fired when the holder deactivates this object.

Currently, releasing the left mouse button triggers deactivation.

### [BindableEvent] GrabbedEvent

Fired when the object is grabbed. The character that grabbed the object is passed as the first argument.

### [BindableEvent] GrabReleasedEvent

Fired when the grab is released.
