# RBX Grab

## Searching Algorithm

For each of these objects, the system first checks the grabbed Part.

Checking an instance will
1. Return a direct child with the matching Name and Class.
2. If an ObjectValue with the matching Name is present, return its Value. (Useful for directing search to an Attachment in a specific Part)
3. Check the instance's Parent, if it's not the Workspace.

A common pattern is to group several Parts into a Model and put all of the relevant grab APIs as children of the Model.

## [Attachment] GrabHint

Hints that the object is intended to be held such that the character's hand CFrame matches the GrabHint's.

## [Attachment] Aim

Hints that this objects is intended to be held such that the Attachment referenced by Aim points at a location the player is targetting.

For example, a pistol would have an Aim ObjectValue that references an Attachment aligned down the barrel so the player knows to point the pistol at the mouse.

## [BindableEvent] ActivatedEvent

Fired when the holder activates this object.

TODO: Can I switch to a BoolValue?
(Is there any problem with out of order property replication.)

## [BindableEvent] DeactivatedEvent

## [BindableEvent] GrabReleasedEvent

Fired when the grab is released.
