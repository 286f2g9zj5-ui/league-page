<script>
    import { yahooHistory } from '$lib/utils/yahooHistory';

    const seasons = [...yahooHistory].sort((a, b) => b.season - a.season);
</script>

<style>
    .history {
        position: relative;
        z-index: 1;
        width: 96%;
        max-width: 1050px;
        margin: 7em auto 10em;
    }

    h1, .intro {
        text-align: center;
    }

    .intro {
        color: #777;
        max-width: 760px;
        margin: 0 auto 3em;
        line-height: 1.5em;
    }

    .season {
        margin: 3em 0;
    }

    .seasonHeader {
        display: flex;
        justify-content: space-between;
        align-items: baseline;
        gap: 1em;
        margin-bottom: 0.75em;
    }

    .platform, .note {
        color: #888;
    }

    .tableWrap {
        overflow-x: auto;
        border: 1px solid var(--d7d7d7);
        border-radius: 6px;
    }

    table {
        width: 100%;
        border-collapse: collapse;
        min-width: 760px;
        background: var(--fff);
    }

    th, td {
        padding: 0.8em 0.65em;
        border-bottom: 1px solid var(--ddd);
        text-align: right;
        white-space: nowrap;
    }

    th {
        font-size: 0.85em;
        color: #777;
    }

    th:nth-child(2), td:nth-child(2), th:nth-child(3), td:nth-child(3) {
        text-align: left;
    }

    tbody tr:last-child td {
        border-bottom: 0;
    }

    .rank {
        font-weight: 700;
    }

    .playoff {
        font-size: 0.75em;
        margin-left: 0.35em;
    }

    .note {
        font-size: 0.85em;
        line-height: 1.4em;
        margin-top: 0.8em;
    }
</style>

<div class="history">
    <h1>NFFFFL History</h1>
    <p class="intro">The permanent record of the NFFFFL across platforms. Sleeper powers the current league; archived Yahoo seasons are added here from historical league records as they are recovered.</p>

    {#each seasons as season}
        <section class="season">
            <div class="seasonHeader">
                <h2>{season.season} Regular Season</h2>
                <span class="platform">{season.platform}</span>
            </div>

            <div class="tableWrap">
                <table>
                    <thead>
                        <tr>
                            <th>Rank</th>
                            <th>Team</th>
                            <th>Division</th>
                            <th>W-L-T</th>
                            <th>Div</th>
                            <th>PF</th>
                            <th>PA</th>
                            <th>Streak</th>
                            <th>Moves</th>
                        </tr>
                    </thead>
                    <tbody>
                        {#each season.teams as team}
                            <tr>
                                <td class="rank">{team.rank}</td>
                                <td>{team.teamName}{#if team.clinchedPlayoffSpot}<span class="playoff" title="Clinched playoff spot">★</span>{/if}</td>
                                <td>{team.division}</td>
                                <td>{team.wins}-{team.losses}-{team.ties}</td>
                                <td>{team.divisionWins}-{team.divisionLosses}-{team.divisionTies}</td>
                                <td>{team.pointsFor.toFixed(2)}</td>
                                <td>{team.pointsAgainst.toFixed(2)}</td>
                                <td>{team.streak}</td>
                                <td>{team.moves}</td>
                            </tr>
                        {/each}
                    </tbody>
                </table>
            </div>

            <p class="note">★ Yahoo marked the team as having clinched a playoff spot. Championship and final playoff placement are intentionally not inferred from this standings snapshot.</p>
        </section>
    {/each}
</div>
