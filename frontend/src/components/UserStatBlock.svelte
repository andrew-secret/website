<script lang="ts">
  import { blur } from 'svelte/transition'
  import Card from './Card.svelte'

  export let rank: number
  export let userStats: UserStats
</script>

<Card let:className>
  <li class={`${className} user-stat-block`} in:blur>
    <p class="rank">#{rank}</p>
    <img
      class="avatar"
      src={userStats.avatarUrl}
      alt="{userStats.user}'s Profile Image"
    />
    <p class="name">{userStats.user}</p>
    <div class="stat-block">
      <p>
        <span class="emoji-stat-light">⚔️️️️️️</span
        >+{userStats.additions}&emsp;-{userStats.deletions}
      </p>
      <p>
        <span class="emoji-stat-light">💾</span>{userStats.commits}
        {userStats.commits === 1 ? 'Commit' : 'Commits'}
      </p>
    </div>
  </li>
</Card>

<style>
  .user-stat-block {
    margin-bottom: 1rem;
    display: grid;
    grid-gap: 2rem;
    grid-template-columns: 3.75rem 6rem 8.365rem 3fr;
    grid-template-areas: 'rank avatar name stats';
  }

  .rank {
    font-size: 2rem;
    opacity: 0.8;
    grid-area: rank;
    align-self: center;
  }

  .avatar {
    border-radius: 50%;
    width: 6rem;
    height: 6rem;
    grid-area: avatar;
    align-self: center;
  }

  .name {
    grid-area: name;
    align-self: center;
  }

  .stat-block {
    grid-area: stats;
    align-self: center;
  }

  .emoji-stat-light {
    font-size: 1.25rem;
    margin-right: 1rem;
    opacity: 0.8;
  }
</style>
