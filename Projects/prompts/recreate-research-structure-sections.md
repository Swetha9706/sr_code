# Task: Recreate two sections in the Krētha case study draft

## Before you start
Read `CLAUDE.md`, `DESIGN.md`, and `PRODUCT.md` first.

Work only on `kretha.html` (the in-progress draft). Do not touch `kretha_copy.html` (the live version).

## What you're replacing

Find the section with the eyebrow "How did research shape the design?" In the current file this single section holds the finding→decision map together with the "connected system" / relationships content that follows it.

Replace that entire section with the two sections below, in order, separated by a `<div class="divider"></div>` exactly as shown. This splits the old single section into two: one on the research → design-decision mapping, one on the platform's structure.

Do not touch any other section (the hero, "What problem am I solving?", "What was my role, exactly?", "What did I design?", "What held it together?", "What did I learn?", etc.). Leave everything before and after this section exactly as it is.

## Target HTML

```html
<section>
  <div class="eyebrow" data-sr>How did research shape the design?</div>
  <h2 class="q-title" data-sr>I mapped the journey <em>before I mapped the screens</em></h2>
  <p class="body" data-sr="1">I mapped the workflows, the roles and their relationships, and the decision paths for key procurement events: order creation, supplier review, changes, confirmations, and follow-up after an order.</p>

  <div class="embed-block" data-sr="1">
    <div class="method-label">Service Blueprint · FigJam</div>
    <h3 class="q-title">How the procurement journey holds together</h3>
    <p class="body">The blueprint maps the journey across three swim lanes: what the retailer does, how the platform responds, and what happens backstage. It makes the dependencies between action and response explicit.</p>
    <a class="embed-figlink" href="https://www.figma.com/board/hoFypYgZl0GxD9iKI6apUd/Customer-Service-Blueprint?node-id=0-1" target="_blank" rel="noopener noreferrer" title="Open the Krētha service blueprint in FigJam">
      <img src="Kr%C4%93tha%20Assets/service-blueprint.png" alt="Krētha service blueprint: swim-lane map of the procurement journey across retailer actions, platform frontstage responses, and backstage processes" loading="lazy" decoding="async" width="5920" height="2220">
      <span class="open-badge">Open in FigJam ↗</span>
    </a>
  </div>

  <p class="body" data-sr="1">Mapping them brought out the real constraints too. The backend dependencies, the phased development, and permission complexity all shaped what the MVP could be.</p>
  <p class="led-note" data-sr="1"><span class="flag">NEEDS REAL NUMBER</span> Workflows and roles mapped during discovery. Swetha: add real counts (sessions held, workflows or roles mapped) if available.</p>

  <div class="map" data-sr="1">
    <div class="map-head">
      <span class="map-k">Finding</span>
      <span></span>
      <span class="map-k map-k--dec">Design decision</span>
    </div>
    <p class="body" data-sr="1" style="margin-bottom:1rem">Each finding from research pointed to a specific design decision. Here's the direct mapping.</p>
    <div class="map-row">
      <div class="map-find"><span class="map-k">Finding</span><p>Procurement is collaborative and distributed across people and time</p></div>
      <div class="map-arrow">→</div>
      <div class="map-dec"><span class="map-k">Design decision</span><p>Role-aware accounts and organisation-level structure with approval logic, so preparing, reviewing, and confirming an order can live with different people, not one.</p></div>
    </div>
    <div class="map-row">
      <div class="map-find"><span class="map-k">Finding</span><p>Repeat ordering is the strongest behavioural pattern in retail</p></div>
      <div class="map-arrow">→</div>
      <div class="map-dec"><span class="map-k">Design decision</span><p>Purchase Lists as first-class, reusable procurement assets (not temporary carts), so routine buying starts with fewer clicks and less reliance on memory.</p></div>
    </div>
    <div class="map-row">
      <div class="map-find"><span class="map-k">Finding</span><p>Business users need reviewability and control, not just speed</p></div>
      <div class="map-arrow">→</div>
      <div class="map-dec"><span class="map-k">Design decision</span><p>A multi-step order flow with draft, review, edit, and approval states before submission, rather than a compressed consumer-style checkout.</p></div>
    </div>
    <div class="map-row">
      <div class="map-find"><span class="map-k">Finding</span><p>MSMEs need something light, not enterprise-heavy</p></div>
      <div class="map-arrow">→</div>
      <div class="map-dec"><span class="map-k">Design decision</span><p>Tiered subscriptions and progressive disclosure: lightweight access for small teams, more coordination capability as an organisation scales.</p></div>
    </div>
    <div class="map-row">
      <div class="map-find"><span class="map-k">Finding</span><p>The platform serves multiple business actors who share information</p></div>
      <div class="map-arrow">→</div>
      <div class="map-dec"><span class="map-k">Design decision</span><p>Organisation-level identity and role-based permissions built into the architecture from day one, rather than bolted onto an individual-user model.</p></div>
    </div>
  </div>
</section>

<div class="divider"></div>

<section>
  <div class="eyebrow" data-sr>How is the platform structured?</div>
  <h2 class="q-title" data-sr>Kr&#275;tha functions like <em>a connected system</em></h2>
  <p class="body" data-sr="1">Kr&#275;tha isn't a set of separate features. Order placement, purchase history, saved lists, account roles, subscriptions, and supplier interaction all shape one another. Each entity functions on its own, but all of them run at the same time, tied together. So the information architecture had to work as one connected system, not a menu of independent tools.</p>
  <p class="body" data-sr="1">That view changed how I made decisions. An order stopped being a single transaction record. It became part of a lifecycle: intent, internal coordination, supplier response, revisions, and fulfilment. A purchase list stopped being a saved cart. It became a planning object tied to recurring buying, stock, and how efficiently a business runs.</p>
  <p class="body" data-sr="1">The design had to make the relationships between users obvious: who belongs to which organisation, who can prepare an order, who can approve it, and which subscription tier unlocks which features. Getting that clarity right mattered as much as any single screen.</p>

  <div class="layers">
    <div class="layer" data-sr="1">
      <div class="layer-title">One lifecycle, not a series of isolated screens</div>
      <p class="layer-text">Browsing, ordering, editing, approving, fulfilling, and reordering form a single lifecycle. Design decisions had to hold across the whole arc of a procurement event, not just one screen at a time.</p>
    </div>
  </div>

  <!-- Supporting artefact: FigJam -->
  <div class="embed-block" data-sr="1">
    <div class="method-label">Product Flowchart · FigJam</div>
    <h3 class="q-title">How the core objects connect</h3>
    <p class="body">The flowchart mapped how each feature connected to the next, before I drew a single screen. It lays out how accounts, organisations, orders, purchase lists, and subscriptions are structured and linked, and how people move between them based on role and permission.</p>
    <iframe loading="lazy" src="https://embed.figma.com/board/0waIfP1SuceBhxs1WcjJYF/Untitled?node-id=0-28&embed-host=share" allowfullscreen title="Krētha product flowchart (FigJam)"></iframe>
  </div>

  <div class="coda" data-sr="1">
    <div class="coda-label">How the work happened</div>
    <div class="coda-grid">
      <div class="coda-item">
        <div class="coda-title">Feasibility alignment</div>
        <p class="coda-text">Checking early whether an interaction idea was grounded in available data and timelines meant fewer false starts down the line.</p>
      </div>
      <div class="coda-item">
        <div class="coda-title">Constraint-based iteration</div>
        <p class="coda-text">Backend and state constraints became a design tool that sharpened decisions, rather than a blocker to work around.</p>
      </div>
      <div class="coda-item">
        <div class="coda-title">Handoff clarity</div>
        <p class="coda-text">Documenting behaviours, conditions, and edge cases kept implementation close to intent as the build progressed.</p>
      </div>
    </div>
  </div>
</section>
```

## If the file doesn't match this description

If the section you find under "How did research shape the design?" doesn't contain a finding→decision map and connected-system content roughly as described, stop and describe what you found instead of guessing at the replacement.

## Constraints
- This is a full block replacement of the identified section only. Do not touch any other section.
- Do not fabricate any stat, count, or credential beyond what's in the target HTML above.
- Confirm the diff before considering this done.
