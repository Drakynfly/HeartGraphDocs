# Widget Input Handler

The class `UHeartWidgetInputHandlerAsset`, is the base class for UMG event handling.

Assets created from children of this class are refered to as WIHs for short (pronounced Wee-z).

It is conceptually similar to an Input Action asset from Enhanced Input, with the major different being that WIH classes can be subclassed to define specific types of events that can occur in UI, the major two being: Actions, and DDOs (Drag Drop Operations).

New WIHs can be created from the right click menu via Heart -> Widget Input Handler, and a class picker will allow for selection of the subtype of event.

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption><p>Default WIHs available in the Content Folder of Heart</p></figcaption></figure>

