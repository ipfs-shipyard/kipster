# Concept

Kipster - A hackable knowledge base for the decentralised web.

## Vision

An open and connected data structure of knowledge that can be visualised and edited in a decentralised fashion.

## Mission

TODO: how do we think we'll get there?

## Positioning

TODO

## Architecture

- Every user has a root of its own tree.
- Every node in a tree is as important as any other node.
- Each node can be seen as a "root" of the underlying tree.
- Each node has a payload, which is handled differently depending on the type.
- Plugins can be added to support additional node types.
- Node types are versioned, to support evolution of the standard.
- Nodes implement a set of patterns (behaviours) to expose functionality:
  - `URL`: Make a node "addressable".
  - `Key-value`: A key value storage for that node.
  - `Discussion`: Commenting on the node.
  - `Request-for-change`: A request for change of the node contents.
  - `Navigation` (optional): Make the node itself visible in the navigation tree and expose underlying navigation data. Navigation nodes can have a title, icon and description.
  - `Display` (optional): Make the node presentable inside a page.
  - `Indexable` (optional): Indexing data to support searching for the node.
  - `Text` (optional): Make the node presentable in a text based environment.
  - `Taggable` (optional): Expose underlying tagging information.
- Nodes that do not implement optional functionality do not provide it.
- A node that implements a pattern can be referred to as its behaviour, as in "a Display node", means a node, regardless of the type, that implements the Display pattern.
- Page nodes are Navigation nodes by default.
- Pages are editable, and contain Display nodes.
- Display nodes can be block or inline.
- Nodes can link to any node, inside or outside the tree, meaning it can link to other users' tree nodes.
- Nodes are encrypted, and the keys are shared with the users who have access.
- Each user device requires not only a user key, but also a device key, in order to mark the node as "synced", to support history compaction.
- Last one to "sync" does the compaction for everyone.
- There is a time/change/size hard limit for compaction, after which, compaction happens automatically for everyone, potentially losing history, in exchange of performance and resources.
- Basic functionality is supported first by local device, then by decentralised service.
- Augmented functionality is supported first by decentralised service, then by centralised service.
- Centralised services can be self-hosted (full control) or cloud based (managed).
- Self-hosted services are open source.

## UX

- Users can browse a tree, whether it is synced to their device or not.
- Users can link to a node outside their tree.
- There are different roles associated with a node, owner, edit and view.
- Owners can remove ANY role from other users.
- Users can opt to "sync" nodes outside their tree, meaning they hold a copy of the data, recursively in that tree.
- If the user has permission to edit a node, other users syncing will receive those changes.
- If the user does not have permission to edit a node, they are prompted to fork the tree.
- Nodes that are not synced, are just being "browsed".
- Users can opt for syncing a node, but granularly opt out of syncing in nodes of that tree, either manually, or by automated policies (security, etc).
- Pages can have templates associated with them, which make it easier to create new pages. Templates are inherited down the tree (cascading), and can be reset on any node.
- Pages can have stylesheets associated with them, which customise their appearance. Stylesheets are inherited down the tree (cascading), and can be reset on any node.
- Any feature that relies on cascading must be accessory for the normal functioning of the page, since any node can be synced into any point of any other tree, meaning that the upstream metadata reference (templates and stylesheets) is lost.
- Plugins can be automatically suggested when a node of an unsupported type is found. If the plugin is not available, a default "unsupported" element is presented. **Consider web assembly and web components. Raises security issues. Look up Jupyter.**
- Users have an "updates feed" available, in order to catch up on changes.
- Users can selectively mute nodes that they are not interested in seeing changes pop up in the feed.
- Users can disable a specific pattern (behaviour) of a node.
- "How do users pick the place to pin a node? (local device, others)"

## Terminology

- Knowledge base: TODO
- Node: A data structure that has a type and a payload, representing a concept within the knowledge base. A page is represented by a node, and its payload contains all the information in the page.
- Node tree: The tree composed of every linked node. A parent will link to the children, but not the other way around.
- Navigation tree: The tree of nodes that generate an entry in a "file system fashion", which are called *navigation nodes*. All pages are listed as folders/files in this tree, as well as a few other node types, like tables. A navigation node requires a title and an icon, but can also have other information, like a description.
- Navigation node: See *Navigation tree*.
- Display node: Nodes that are presentable inside a page.
