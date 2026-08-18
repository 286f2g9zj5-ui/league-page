<script>
    const details = [
        { label: 'Date', value: 'TBD' },
        { label: 'Time', value: 'TBD' },
        { label: 'Location', value: 'TBD' },
        { label: 'League Dues', value: '$150' },
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

    .subtitle, p, li {
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

    .commissioner {
        font-style: italic;
        font-size: 1.05em;
    }

    .payoutGrid {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        gap: .75em 1.5em;
        margin-top: 1em;
    }

    .payout {
        display: flex;
        justify-content: space-between;
        border-bottom: 1px solid var(--ddd);
        padding: .55em 0;
        color: #777;
    }

    .payout strong {
        color: var(--g555);
    }

    @media (max-width: 700px) {
        h1 { font-size: 2em; }
        .details, .payoutGrid { grid-template-columns: repeat(2, 1fr); }
    }
</style>

<div class="page">
    <header class="hero">
        <div class="eyebrow">NFFFFL Draft Headquarters</div>
        <h1>2027 Draft</h1>
        <p class="subtitle">Everything the league needs to know about the 2027 NFFFFL Draft and the season ahead.</p>
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
        <h2>From the Commissioner</h2>
        <p class="commissioner">Another incredible NFFFFL draft weekend, boys. It remains an honor to serve as your leader, authoritarian, dictator, daddy, and — most importantly — humble commissioner.</p>
    </section>

    <section class="section">
        <h2>Schedule Format</h2>
        <ul>
            <li><strong>Rivalry Week</strong> opens the season in Week 1 and returns for the final week of the regular season.</li>
            <li>Teams play their division opponents during the <strong>first three and last three games</strong> of the schedule.</li>
            <li>Division opponents should not appear elsewhere on the schedule.</li>
        </ul>
    </section>

    <section class="section">
        <h2>Division Privileges</h2>
        <p>Last season's division leaders get naming rights. Each division leader may choose the division name and picture, and those can be changed at any time.</p>
    </section>

    <section class="section">
        <h2>FAAB</h2>
        <p>Every owner begins with a <strong>$100 FAAB budget</strong>. The minimum bid is <strong>$1</strong>. FAAB is fantasy currency only — there are no real-money implications.</p>
    </section>

    <section class="section">
        <h2>Dues & Payouts</h2>
        <p>League dues are <strong>$150 per owner</strong>, creating a total league pot of <strong>$1,800</strong>.</p>
        <div class="payoutGrid">
            <div class="payout"><span>Champion</span><strong>$1,000</strong></div>
            <div class="payout"><span>Runner-Up</span><strong>$200</strong></div>
            <div class="payout"><span>Division Winner</span><strong>$100 each</strong></div>
            <div class="payout"><span>Rivalry Winner</span><strong>$50 each</strong></div>
        </div>
    </section>

    <section class="section">
        <h2>Draft Weekend</h2>
        <p>The 2027 draft will bring all 12 NFFFFL owners together for another season of bad predictions, questionable reaches, stolen picks, and decisions that will be brought up long after the draft board comes down.</p>
        <p>Date, location, arrival plans, lodging, food, and other draft-weekend details will be posted here as they are finalized.</p>
    </section>

    <section class="section">
        <h2>Draft Order</h2>
        <p>The official 2027 draft order has not been posted here yet. Once confirmed, this section can show all 12 owners in order along with traded picks and other draft-pick notes.</p>
    </section>
</div>
