<script>
    import { meetTheTeamOwners } from '$lib/utils/meetTheTeam';

    let selectedIndex = 0;
    $: selected = meetTheTeamOwners[selectedIndex];

    const previous = () => selectedIndex = (selectedIndex - 1 + meetTheTeamOwners.length) % meetTheTeamOwners.length;
    const next = () => selectedIndex = (selectedIndex + 1) % meetTheTeamOwners.length;
</script>

<style>
    .page { position: relative; z-index: 1; width: 94%; max-width: 1150px; margin: 7em auto 10em; }
    h1 { margin-bottom: .25em; font-size: 2.4em; }
    .subtitle { color: #888; margin-bottom: 2em; }
    .controls { display: flex; gap: .75em; align-items: center; margin-bottom: 1.5em; }
    select, button { background: var(--f8f8f8); color: inherit; border: 1px solid var(--d7d7d7); border-radius: 6px; padding: .75em 1em; font: inherit; }
    select { min-width: 230px; }
    button { cursor: pointer; }
    .layout { display: grid; grid-template-columns: 250px 1fr; gap: 1.5em; }
    .owners, .profile { border: 1px solid var(--d7d7d7); border-radius: 8px; overflow: hidden; background: var(--f8f8f8); }
    .ownersTitle { padding: 1em; font-weight: 700; border-bottom: 1px solid var(--d7d7d7); }
    .owner { width: 100%; border: 0; border-radius: 0; text-align: left; padding: .9em 1em; border-bottom: 1px solid var(--d7d7d7); background: transparent; }
    .owner.active { font-weight: 700; background: rgba(146, 5, 5, .12); }
    .commissioner { display: block; font-size: .75em; color: #888; margin-top: .25em; }
    .profile { padding: 2em; }
    .profileTop { display: grid; grid-template-columns: 180px 1fr; gap: 2em; align-items: center; }
    .photo { width: 180px; height: 180px; border-radius: 50%; object-fit: cover; border: 2px solid var(--d7d7d7); }
    .placeholderPhoto { width: 180px; height: 180px; border-radius: 50%; border: 2px solid var(--d7d7d7); display: grid; place-items: center; font-size: 4em; color: #888; }
    .name { font-size: 2.2em; margin: 0 0 .2em; }
    .role { color: #920505; font-weight: 600; }
    .stats { display: grid; grid-template-columns: repeat(2, minmax(120px, 1fr)); gap: 1em; margin-top: 1.5em; }
    .stat { border-top: 1px solid var(--d7d7d7); padding-top: .8em; }
    .label { display: block; color: #888; font-size: .8em; text-transform: uppercase; letter-spacing: .05em; }
    .value { display: block; font-size: 1.35em; font-weight: 700; margin-top: .25em; }
    .background { margin-top: 2em; padding-top: 1.5em; border-top: 1px solid var(--d7d7d7); }
    .background p { color: #777; line-height: 1.6em; }
    .empty { font-style: italic; }
    @media (max-width: 760px) {
        .layout { grid-template-columns: 1fr; }
        .owners { display: none; }
        .profileTop { grid-template-columns: 1fr; text-align: center; }
        .photo, .placeholderPhoto { margin: auto; }
        .stats { text-align: left; }
        .controls { justify-content: center; flex-wrap: wrap; }
    }
</style>

<div class="page">
    <h1>Meet the Team</h1>
    <p class="subtitle">The 12 owners. The rivalries. The stories behind the NFFFFL.</p>

    <div class="controls">
        <button onclick={previous} aria-label="Previous owner">‹</button>
        <select bind:value={selectedIndex} aria-label="Select league owner">
            {#each meetTheTeamOwners as owner, index}
                <option value={index}>{owner.name}{owner.commissioner ? ' — Commissioner' : ''}</option>
            {/each}
        </select>
        <button onclick={next} aria-label="Next owner">›</button>
        <span>{selectedIndex + 1} of {meetTheTeamOwners.length}</span>
    </div>

    <div class="layout">
        <aside class="owners">
            <div class="ownersTitle">League Owners (12)</div>
            {#each meetTheTeamOwners as owner, index}
                <button class:active={selectedIndex === index} class="owner" onclick={() => selectedIndex = index}>
                    {owner.name}
                    {#if owner.commissioner}<span class="commissioner">Commissioner</span>{/if}
                </button>
            {/each}
        </aside>

        <section class="profile">
            <div class="profileTop">
                {#if selected.photo}
                    <img class="photo" src={selected.photo} alt={`${selected.name} profile`} />
                {:else}
                    <div class="placeholderPhoto" aria-label="Photo coming soon">?</div>
                {/if}

                <div>
                    <h2 class="name">{selected.name}</h2>
                    {#if selected.commissioner}<div class="role">NFFFFL Commissioner</div>{/if}
                    <div class="stats">
                        <div class="stat">
                            <span class="label">Age</span>
                            <span class="value">{selected.age ?? '—'}</span>
                        </div>
                        <div class="stat">
                            <span class="label">Average Finish</span>
                            <span class="value">{selected.averageFinish ?? '—'}</span>
                        </div>
                    </div>
                </div>
            </div>

            <div class="background">
                <h3>Background</h3>
                {#if selected.background}
                    <p>{selected.background}</p>
                {:else}
                    <p class="empty">Profile coming soon. This owner’s biography, league history, and photo will be added as the NFFFFL archive is completed.</p>
                {/if}
            </div>
        </section>
    </div>
</div>
