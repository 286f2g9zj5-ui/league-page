<script>
    const details = [
        { label: 'Date', value: 'TBD' },
        { label: 'Time', value: 'TBD' },
        { label: 'Location', value: 'TBD' },
        { label: 'Draft Format', value: 'TBD' },
    ];
</script>

<style>
    .page {
        position: relative;
        z-index: 1;
        width: 92%;
        max-width: 900px;
        margin: 7em auto 10em;
    }

    .hero {
        text-align: center;
        margin-bottom: 3em;
    }

    .eyebrow {
        text-transform: uppercase;
        letter-spacing: .16em;
        font-size: .8em;
        color: #920505;
        font-weight: 700;
    }

    h1 {
        font-size: 2.6em;
        margin: .25em 0;
    }

    .subtitle, p {
        color: #777;
        line-height: 1.6em;
    }

    .details {
        display: grid;
        grid-template-columns: repeat(4, 1fr);
        gap: 1em;
        margin: 2em 0 3em;
    }

    .card, .section {
        border: 1px solid var(--d7d7d7);
        border-radius: 8px;
        background: var(--fff);
        box-shadow: 0 2px 6px var(--boxShadowThree);
    }

    .card {
        padding: 1.25em;
        text-align: center;
    }

    .label {
        display: block;
        color: #888;
        font-size: .8em;
        text-transform: uppercase;
        letter-spacing: .08em;
        margin-bottom: .5em;
    }

    .value {
        font-weight: 700;
        font-size: 1.1em;
    }

    .section {
        padding: 1.5em 1.75em;
        margin: 1.25em 0;
    }

    h2 {
        margin-top: 0;
    }

    .status {
        display: inline-block;
        padding: .4em .75em;
        border: 1px solid #920505;
        border-radius: 999px;
        color: #920505;
        font-weight: 600;
        font-size: .85em;
    }

    @media (max-width: 700px) {
        h1 { font-size: 2em; }
        .details { grid-template-columns: repeat(2, 1fr); }
    }
</style>

<div class="page">
    <header class="hero">
        <div class="eyebrow">NFFFFL Draft Headquarters</div>
        <h1>2027 Draft</h1>
        <p class="subtitle">Everything the league needs to know about the 2027 NFFFFL Draft will live here.</p>
        <span class="status">Planning in progress</span>
    </header>

    <div class="details">
        {#each details as detail}
            <div class="card">
                <span class="label">{detail.label}</span>
                <span class="value">{detail.value}</span>
            </div>
        {/each}
    </div>

    <section class="section">
        <h2>Draft Weekend</h2>
        <p>The 2027 draft will bring all 12 NFFFFL owners together for another season of bad predictions, questionable reaches, stolen picks, and decisions that will be brought up long after the draft board comes down.</p>
        <p>Date, location, arrival plans, lodging, food, and other draft-weekend details will be posted here as they are finalized.</p>
    </section>

    <section class="section">
        <h2>Draft Order</h2>
        <p>The official 2027 draft order has not been posted here yet. Once confirmed, this section can show all 12 owners in order along with traded picks and other draft-pick notes.</p>
    </section>

    <section class="section">
        <h2>Rules & Format</h2>
        <p>Draft format, number of rounds, pick timer, keeper or dynasty implications, and any special NFFFFL draft rules will be added once confirmed. Sleeper remains the authoritative source for active league settings.</p>
    </section>

    <section class="section">
        <h2>What to Bring</h2>
        <p>This section is reserved for the practical stuff: what owners need to bring, payment reminders, food and drink plans, draft-board information, and anything else Kevin decides everyone should have known before showing up.</p>
    </section>
</div>
