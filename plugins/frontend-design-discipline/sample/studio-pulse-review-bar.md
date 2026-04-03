# Studio Pulse Review Bar

## Overall Pass Condition

- the first viewport cannot be mistaken for a generic task-management SaaS page
- the page reads as a quiet, precise release workspace rather than a marketing dashboard
- hierarchy is legible without explanatory copy doing all the work
- each section has one dominant subject and one clear job
- typography, color, and imagery all point in the same direction
- the close feels decisive and calm rather than salesy or vague

## First View Must-Haves

- the hero reads as one composition, not two equal columns negotiating for attention
- there is a real visual anchor, not just a weak mockup or decorative gradient
- the product name and promise are unmistakable in one glance
- the headline scale feels intentional and controlled, not oversized to compensate for weak art direction
- lower-section headings and proof blocks do not overwrap into repetitive mini-columns
- the page already feels unlike Notion templates, Linear clones, or generic B2B homepages

## Reject Immediately If

- the first impression is a card grid
- the hero is left text plus right mockup with no real visual dominance
- the hero headline is so large that support copy, CTA, or brand presence get visually crushed
- lower sections depend on awkward 2-line/3-line wrapping patterns across multiple sibling blocks
- the design depends on multiple paragraphs to explain why it is special
- lower sections look like interchangeable marketing blocks
- the accent color behaves like decoration instead of signal
- the CTA cluster feels like two random buttons instead of a conclusion

## Critic Routing

### Preflight

- use `frontend-preflight-critic`
- fail the direction if the packet does not clearly prevent a generic SaaS outcome

### Brand

- use `frontend-brand-critic`
- fail if the page could belong to almost any B2B product

### Composition

- use `frontend-composition-critic`
- fail if the page reads as rows of blocks instead of an editorial composition

### Copy

- use `frontend-copy-critic`
- fail if the wording has to compensate for weak visuals

### UI Stability

- use `frontend-ui-auditor`
- fail if the proposed or actual layout looks one breakpoint away from breaking
