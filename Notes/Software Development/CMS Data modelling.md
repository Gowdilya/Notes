https://medium.com/@H_Stahl/a-beginners-guide-to-headless-content-modeling-part-1-core-concepts-d053feaec354

1. **Content is separate from context**. _Content_ is the data needed to represent business entities and _context_ is how you display that content.
2. **Content types are well-structured**. Content types consist of well-defined attributes and properties, as well as relationships between different entities.

In traditional setups and monolithic CMSes, we fixate on the interface — a website, a mobile device, a digital screen. This interface-centric thinking is what often leads us to trouble. Headless content management aims to fix that. We plan and connect our content outside of the interface, and by doing that — it’s ready for _any_ interface. This is called decoupling, and a decoupled content model is agnostic.

## Why is Structured & Agnostic Content Important?

**Reusability**

- Structured and agnostic content makes your content easy to reuse. Instead of having to copy and paste the exact same content to fit specific interfaces, decoupled content can be created once and then published everywhere. Duplicating content is wasteful, so the goal is basically to avoid duplicating content. A decoupled content model is what we call _agnostic_, because it does not know and it does not care about the interface consuming it.

**Speed and Cost**

- Structured and agnostic content is cheaper, because it saves time — and time is money. When working with coupled content data, every single visual component as well as the subject matter must be redesigned when doing e.g. a website redesign, instead of focusing solely on the visual redesign when working with decoupled content data.

**Adaptability**

- Structured and agnostic content makes your content future-friendly. Structuring your content makes it ready to adapt to technologies that are not screen-centric such as smart speakers, wearables, voice-recognition devices, and so on.

Let’s look at a classic comparison between well-structured content and poorly structured content:![[Screenshot 2023-08-14 at 1.37.44 PM.png]]

The **article** or **blog post** is a very straight-forward use case because we so often encounter them, either as writers or readers (or both). In this example of a poorly structured article, every single building block is crammed into the same content type with all information packed into the same field, and there are no defined relationships between these pieces of information. This means that it will be very hard to extract the data and use it elsewhere; it’s not reusable. If an author writes multiple articles — which happens more often than not — you would have to duplicate the author information in the other articles.


One way to repurpose this data would be to simply extract every piece of information into separate fields. That would make things cleaner, but the data would still be exclusive to this particular content type. We would have no way of reusing the author field in another content type, other than by — you guessed it — duplicating it.![[Screenshot 2023-08-14 at 1.39.03 PM.png]]
## Content Modeling Vocabulary

Here’s a list of common terms you’ll come across in the realms of headless content management and content modeling:

- **Content Model:** The overall architecture of your content. It consists of chunks we call content types. In other words, a content model is a collection of content types.
- **Content Type:** The structure or _container_ for a piece of content. A content type is made up of different fields of information.
- **Fields (aka attributes):** Represents different properties or characteristics for a piece of content. Each field will be assigned a data type such as text, rich text, number, date, location, media asset, boolean, JSON object, reference, etc.
- **Entry:** A piece of content based on a content type. You might think of an entry as an “instance” of that content type. For example, an individual article or blog post is an _article entry_. I.e, an instance of the article/blog post content type.
- **Reference:** A link between two content types via a field. A reference creates a relationship between two different content types. For example, an article can reference an author; the article content type and the author content type now have an interrelationship.
- **Headless:** The concept of chopping the “head” (frontend) off the “body” (backend). I.e, a clean separation between content and context.
- **Decoupling/decoupled:** The act of separating content from context. A “decoupled frontend” is basically a frontend application that has been separated from the CMS.
- **Agnostic:** When we refer to something as _agnostic_, it means that it is unaware of the interface consuming it. The interface might be a visual one, or a non-visual one. The agnostic content model doesn’t know and it doesn’t care, because content is separated from context.