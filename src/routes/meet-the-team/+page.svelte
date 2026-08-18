<script>
    import { meetTheTeamOwners } from '$lib/utils/meetTheTeam';

    let selectedIndex = $state(0);
    let selected = $derived(meetTheTeamOwners[selectedIndex]);

    const selectOwner = (index) => {
        selectedIndex = Number(index);
    };

    const previous = () => {
        selectedIndex = (selectedIndex - 1 + meetTheTeamOwners.length) % meetTheTeamOwners.length;
    };

    const next = () => {
        selectedIndex = (selectedIndex + 1) % meetTheTeamOwners.length;
    };

    const initials = (name) => name.split(' ').map((part) => part[0]).join('').slice(0, 2).toUpperCase();
    const paragraphs = (text) => String(text || '').split(/\n\s*\n/).filter(Boolean);
</script>

<style>
    .page {
        position: relative;
        z-index: 1;
        width: 94%;
        max-width: 1220px;
        margin: 6.5em auto 12em;
        padding-bottom: 4em;
    }

    .pageHeader {
        display: flex;
        align-items: flex-end;
        justify-content: space-between;
        gap: 2em;
        margin-bottom: 2em;
    }

    .eyebrow {
        display: block;
        color: #920505;
        font-size: .78em;
        font-weight: 800;
        letter-spacing: .16em;
        text-transform: uppercase;
        margin-bottom: .6em;
    }

    h1 {
        margin: 0;
        font-size: clamp(2.5em, 5vw, 4.25em);
        line-height: .95em;
        letter-spacing: -.035em;
    }

    .subtitle {
        color: #888;
        margin: .8em 0 0;
        font-size: 1.05em;
    }

    .pager {
        display: flex;
        align-items: center;
        border: 1px solid var(--d7d7d7);
        border-radius: 999px;
        background: var(--f8f8f8);
        overflow: hidden;
        flex-shrink: 0;
    }

    .pager button {
        border: 0;
        background: transparent;
        color: #920505;
        cursor: pointer;
        font-size: 1.7em;
        width: 46px;
        height: 46px;
    }

    .pagerCount {
        min-width: 72px;
        text-align: center;
        font-size: .85em;
        font-weight: 700;
        color: #777;
    }

    .layout {
        display: grid;
        grid-template-columns: 285px minmax(0, 1fr);
        gap: 1.4em;
        align-items: start;
    }

    .owners {
        border: 1px solid var(--d7d7d7);
        border-radius: 14px;
        background: var(--f8f8f8);
        overflow: hidden;
        box-shadow: 0 8px 30px var(--boxShadowThree);
    }

    .ownersTitle {
        padding: 1.1em 1.15em;
        font-size: .78em;
        font-weight: 800;
        letter-spacing: .1em;
        text-transform: uppercase;
        color: #888;
        border-bottom: 1px solid var(--d7d7d7);
    }

    .owner {
        display: grid;
        grid-template-columns: 42px minmax(0, 1fr) auto;
        gap: .8em;
        align-items: center;
        width: 100%;
        border: 0;
        border-bottom: 1px solid var(--d7d7d7);
        border-radius: 0;
        text-align: left;
        padding: .8em 1em;
        background: transparent;
        color: inherit;
        cursor: pointer;
    }

    .owner:last-child { border-bottom: 0; }
    .owner:hover { background: rgba(146, 5, 5, .06); }
    .owner.active {
        background: linear-gradient(90deg, rgba(146, 5, 5, .16), rgba(146, 5, 5, .05));
        box-shadow: inset 4px 0 0 #920505;
    }

    .ownerAvatar, .placeholderPhoto {
        display: grid;
        place-items: center;
        border-radius: 50%;
        overflow: hidden;
        background: var(--ddd);
        color: #666;
        font-weight: 800;
    }

    .ownerAvatar {
        width: 42px;
        height: 42px;
        font-size: .85em;
    }

    .ownerAvatar img {
        width: 100%;
        height: 100%;
        object-fit: cover;
    }

    .ownerName {
        display: block;
        font-weight: 800;
        line-height: 1.15em;
    }

    .ownerTeam {
        display: block;
        color: #888;
        font-size: .78em;
        margin-top: .25em;
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
    }

    .commishBadge {
        display: inline-grid;
        place-items: center;
        width: 24px;
        height: 24px;
        border-radius: 50%;
        background: #920505;
        color: #fff;
        font-size: .72em;
        font-weight: 800;
    }

    .profile {
        position: relative;
        border: 1px solid var(--d7d7d7);
        border-radius: 16px;
        background: var(--f8f8f8);
        box-shadow: 0 8px 30px var(--boxShadowThree);
        overflow: visible;
    }

    .profile::before {
        content: '';
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        height: 6px;
        border-radius: 16px 16px 0 0;
        background: #920505;
    }

    .profileHero {
        display: grid;
        grid-template-columns: 220px minmax(0, 1fr);
        gap: 2.2em;
        padding: 2.4em;
        align-items: center;
    }

    .photoWrap {
        position: relative;
        width: 210px;
        height: 210px;
    }

    .photo, .placeholderPhoto {
        width: 210px;
        height: 210px;
        border: 5px solid var(--fff);
        box-shadow: 0 8px 28px var(--boxShadowTwo);
        box-sizing: border-box;
    }

    .photo {
        display: block;
        border-radius: 50%;
        object-fit: cover;
        background: var(--ddd);
    }

    .placeholderPhoto { font-size: 3.6em; }

    .teamChip {
        position: absolute;
        left: 50%;
        bottom: -8px;
        transform: translateX(-50%);
        max-width: 185px;
        padding: .45em .85em;
        border-radius: 999px;
        background: #920505;
        color: #fff;
        font-size: .72em;
        font-weight: 800;
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
        box-shadow: 0 3px 10px var(--boxShadowTwo);
    }

    .profileKicker {
        color: #920505;
        font-size: .76em;
        font-weight: 800;
        letter-spacing: .12em;
        text-transform: uppercase;
        margin-bottom: .5em;
    }

    .name {
        font-size: clamp(2.4em, 5vw, 4em);
        letter-spacing: -.035em;
        line-height: .95em;
        margin: 0;
    }

    .nickname {
        color: #777;
        font-size: 1.05em;
        margin-top: .65em;
        font-style: italic;
    }

    .stats {
        display: grid;
        grid-template-columns: repeat(3, minmax(0, 1fr));
        gap: .8em;
        margin-top: 1.7em;
    }

    .stat {
        border: 1px solid var(--d7d7d7);
        border-radius: 10px;
        padding: .9em 1em;
        background: var(--fff);
        min-width: 0;
    }

    .label {
        display: block;
        color: #888;
        font-size: .7em;
        font-weight: 800;
        text-transform: uppercase;
        letter-spacing: .08em;
    }

    .value {
        display: block;
        font-size: 1.2em;
        font-weight: 800;
        margin-top: .3em;
        overflow-wrap: anywhere;
    }

    .profileBody {
        display: grid;
        grid-template-columns: minmax(0, 1.6fr) minmax(230px, .8fr);
        border-top: 1px solid var(--d7d7d7);
    }

    .bio, .scouting {
        padding: 2em 2.4em 2.6em;
        min-width: 0;
    }

    .scouting {
        border-left: 1px solid var(--d7d7d7);
        background: rgba(146, 5, 5, .035);
        border-radius: 0 0 16px 0;
    }

    .sectionLabel {
        display: flex;
        align-items: center;
        gap: .6em;
        color: #920505;
        font-size: .76em;
        font-weight: 800;
        letter-spacing: .1em;
        text-transform: uppercase;
        margin-bottom: 1em;
    }

    .sectionLabel::before {
        content: '';
        width: 22px;
        height: 2px;
        background: #920505;
    }

    .bio p, .scouting p {
        color: #777;
        line-height: 1.72em;
        margin: 0 0 1.1em;
        overflow-wrap: anywhere;
    }

    .bio p:last-child, .scouting p:last-child { margin-bottom: 0; }
    .scouting p { font-size: .95em; font-weight: 600; }
    .empty { font-style: italic; }

    .mobileRail { display: none; }

    @media (max-width: 900px) {
        .layout { grid-template-columns: 235px minmax(0, 1fr); }
        .profileHero { grid-template-columns: 170px minmax(0, 1fr); gap: 1.5em; padding: 2em; }
        .photoWrap, .photo, .placeholderPhoto { width: 165px; height: 165px; }
        .profileBody { grid-template-columns: 1fr; }
        .scouting { border-left: 0; border-top: 1px solid var(--d7d7d7); border-radius: 0 0 16px 16px; }
        .stats { grid-template-columns: repeat(2, minmax(0, 1fr)); }
    }

    @media (max-width: 700px) {
        .page { width: 92%; margin-top: 5.5em; }
        .pageHeader { align-items: flex-start; }
        .subtitle { font-size: .95em; }
        .layout { display: block; }
        .owners { display: none; }

        .mobileRail {
            display: flex;
            gap: .55em;
            overflow-x: auto;
            padding: .2em 0 .9em;
            margin-bottom: .7em;
            scrollbar-width: none;
        }
        .mobileRail::-webkit-scrollbar { display: none; }

        .mobileOwner {
            flex: 0 0 auto;
            border: 1px solid var(--d7d7d7);
            border-radius: 999px;
            background: var(--f8f8f8);
            color: inherit;
            padding: .55em .85em;
            font: inherit;
            font-size: .82em;
            font-weight: 700;
            cursor: pointer;
        }
        .mobileOwner.active {
            background: #920505;
            border-color: #920505;
            color: #fff;
        }

        .profileHero {
            grid-template-columns: 1fr;
            text-align: center;
            padding: 2em 1.4em 1.6em;
        }
        .photoWrap { margin: 0 auto .8em; }
        .stats { text-align: left; }
        .bio, .scouting { padding: 1.5em; }
    }

    @media (max-width: 470px) {
        .pageHeader { display: block; }
        .pager { margin-top: 1.25em; width: max-content; }
        .stats { grid-template-columns: 1fr 1fr; }
        .stat:last-child { grid-column: 1 / -1; }
        .name { font-size: 2.45em; }
    }
</style>

<div class="page">
    <header class="pageHeader">
        <div>
            <span class="eyebrow">NFFFFL Personnel File</span>
            <h1>Meet the Team</h1>
            <p class="subtitle">The 12 owners. The rivalries. The stories behind the league.</p>
        </div>

        <div class="pager" aria-label="Owner navigation">
            <button type="button" onclick={previous} aria-label="Previous owner">‹</button>
            <span class="pagerCount">{selectedIndex + 1} / {meetTheTeamOwners.length}</span>
            <button type="button" onclick={next} aria-label="Next owner">›</button>
        </div>
    </header>

    <div class="mobileRail" aria-label="Select league owner">
        {#each meetTheTeamOwners as owner, index}
            <button type="button" class="mobileOwner" class:active={selectedIndex === index} onclick={() => selectOwner(index)}>
                {owner.name}
            </button>
        {/each}
    </div>

    <div class="layout">
        <aside class="owners">
            <div class="ownersTitle">League Owners · {meetTheTeamOwners.length}</div>
            {#each meetTheTeamOwners as owner, index}
                <button type="button" class="owner" class:active={selectedIndex === index} onclick={() => selectOwner(index)}>
                    <span class="ownerAvatar">
                        {#if owner.photo}
                            <img src={owner.photo} alt="" />
                        {:else}
                            {initials(owner.name)}
                        {/if}
                    </span>
                    <span>
                        <span class="ownerName">{owner.name}</span>
                        <span class="ownerTeam">{owner.teamName || 'NFFFFL Owner'}</span>
                    </span>
                    {#if owner.commissioner}<span class="commishBadge" title="Commissioner">C</span>{/if}
                </button>
            {/each}
        </aside>

        <section class="profile">
            <div class="profileHero">
                <div class="photoWrap">
                    {#if selected.photo}
                        <img class="photo" src={selected.photo} alt={`${selected.name} profile`} />
                    {:else}
                        <div class="placeholderPhoto" aria-label="Photo coming soon">{initials(selected.name)}</div>
                    {/if}
                    <div class="teamChip">{selected.teamName || 'NFFFFL Owner'}</div>
                </div>

                <div>
                    <div class="profileKicker">{selected.commissioner ? 'Commissioner · League Owner' : 'League Owner'}</div>
                    <h2 class="name">{selected.name}</h2>
                    {#if selected.nickname}<div class="nickname">“{selected.nickname}”</div>{/if}

                    <div class="stats">
                        <div class="stat">
                            <span class="label">Age</span>
                            <span class="value">{selected.age ?? 'TBD'}</span>
                        </div>
                        <div class="stat">
                            <span class="label">Average Finish</span>
                            <span class="value">{selected.averageFinish ?? 'TBD'}</span>
                        </div>
                        <div class="stat">
                            <span class="label">Team</span>
                            <span class="value">{selected.teamName || 'TBD'}</span>
                        </div>
                    </div>
                </div>
            </div>

            <div class="profileBody">
                <div class="bio">
                    <div class="sectionLabel">Background</div>
                    {#if selected.background}
                        {#each paragraphs(selected.background) as paragraph}
                            <p>{paragraph}</p>
                        {/each}
                    {:else}
                        <p class="empty">Biography and league history coming soon. This profile will be expanded as the NFFFFL archive is completed.</p>
                    {/if}
                </div>

                <aside class="scouting">
                    <div class="sectionLabel">Scouting Report</div>
                    {#if selected.scoutingReport}
                        <p>{selected.scoutingReport}</p>
                    {:else}
                        <p class="empty">Scouting report pending.</p>
                    {/if}
                </aside>
            </div>
        </section>
    </div>
</div>
