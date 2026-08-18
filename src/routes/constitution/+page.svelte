<script>
    import { dues } from '$lib/utils/helper';
</script>

<style>
    .constitution {
        position: relative;
        z-index: 1;
        width: 92%;
        max-width: 800px;
        margin: 8em auto 10em;
    }

    h1 {
        font-size: 2em;
        line-height: 1.2em;
        text-align: center;
        margin: 2em 0 0.5em;
    }

    .subtitle {
        text-align: center;
        color: #777;
        margin-bottom: 3em;
    }

    h2 {
        font-size: 1.5em;
        line-height: 1.2em;
        margin-top: 2.5em;
    }

    p, li {
        color: #777;
        line-height: 1.6em;
    }

    .notice {
        border: 1px solid var(--d7d7d7);
        padding: 1.25em 1.5em;
        margin: 2em 0 3em;
        border-radius: 4px;
    }

    .rules {
        padding-left: 1.3em;
    }

    .payouts {
        width: 100%;
        border-collapse: collapse;
        margin: 1em 0;
    }

    .payouts td {
        padding: .65em .4em;
        border-bottom: 1px solid var(--ddd);
        color: #777;
    }

    .payouts td:last-child {
        text-align: right;
        font-weight: 700;
    }

    .closing {
        font-weight: 500;
        margin-top: 3em;
    }
</style>

<div class="constitution">
    <h1>NFFFFL LEAGUE CONSTITUTION</h1>
    <p class="subtitle">The governing principles and confirmed rules of the NFFFFL</p>

    <div class="notice">
        <strong>Living league document.</strong>
        <p>This page records confirmed NFFFFL rules and traditions. Sleeper remains the authoritative source for platform-controlled settings that are not specifically documented here.</p>
    </div>

    <h2>1. League Identity</h2>
    <p>The NFFFFL is a 12-manager fantasy football league built around a group of longtime friends from Fergus Falls, Minnesota. The league exists to combine competitive fantasy football with the rivalries, history, and bragging rights that come from competing against the same group year after year.</p>

    <h2>2. Competition & League Integrity</h2>
    <p>Every manager is expected to compete in good faith throughout the season. Managers control their own teams and are responsible for maintaining competitive lineups, managing their rosters, and making decisions in the best interests of their franchise.</p>
    <p>Collusion, coordinated roster manipulation, or other conduct intended to undermine fair competition is inconsistent with the NFFFFL. Questions that materially affect league integrity should be handled transparently by the commissioner and, when appropriate, the league as a whole.</p>

    <h2>3. Schedule Format</h2>
    <ul class="rules">
        <li><strong>Rivalry weeks:</strong> Week 1 and the final week of the regular-season schedule.</li>
        <li><strong>Division games:</strong> Division opponents are played during the first three and last three games of the schedule.</li>
        <li>Division opponents should not be scheduled against one another outside those designated portions of the schedule.</li>
    </ul>

    <h2>4. Divisions</h2>
    <p>The prior season's division leaders earn the right to choose their division's name and picture for the following season. Division names and images may be changed during the season.</p>

    <h2>5. Free-Agent Acquisition Budget (FAAB)</h2>
    <ul class="rules">
        <li>Each team receives a <strong>$100 FAAB budget</strong>.</li>
        <li>The minimum waiver bid is <strong>$1</strong>.</li>
        <li>FAAB is fantasy currency only and has <strong>no real-money implication</strong>.</li>
    </ul>

    <h2>6. League Dues & Payouts</h2>
    <p>Annual league dues are <strong>${dues} per team</strong>. With 12 teams, the full league pot is <strong>$1,800</strong>.</p>

    <table class="payouts">
        <tbody>
            <tr><td>NFFFFL Champion</td><td>$1,000</td></tr>
            <tr><td>Runner-Up</td><td>$200</td></tr>
            <tr><td>Division Winner</td><td>$100 each</td></tr>
            <tr><td>Rivalry Winner</td><td>$50 each</td></tr>
        </tbody>
    </table>

    <p>With three division winners and six rivalry winners, the listed payouts distribute the full $1,800 league pot.</p>

    <h2>7. Official League Settings</h2>
    <p>The NFFFFL's active Sleeper configuration governs operational settings not expressly documented here, including scoring, starting lineup requirements, roster limits, trade settings, draft configuration, playoff structure, and other platform-controlled rules.</p>

    <h2>8. Rule Changes</h2>
    <p>Material changes to league rules should be communicated to league members before taking effect. Confirmed rules and traditions will be added to this constitution so the site becomes the permanent written record of how the NFFFFL operates.</p>

    <h2>9. League History</h2>
    <p>The NFFFFL predates its move to Sleeper. Historical seasons, championships, standings, records, and other league accomplishments from prior platforms remain part of the official NFFFFL record and will be incorporated into this site as that history is assembled.</p>

    <p class="closing">Twelve friends. One league. Years of receipts.</p>
</div>
