<script>
  import MeetupItem from "./MeetupItem.svelte";
  export let meetups;
</script>

<style>
  section {
    width: 100%;
    display: grid;
    grid-template-columns: 1fr;
    grid-gap: 1rem;
  }

  @media (min-width: 768px) {
    section {
      grid-template-columns: repeat(2, 1fr);
    }
  }
</style>

<section>
  {#each meetups as meetup, i (meetup.id)}
    <MeetupItem
      id={meetup.id}
      title={meetup.title}
      subtitle={meetup.subtitle}
      imageUrl={meetup.imageUrl}
      description={meetup.description}
      address={meetup.address}
      contactEmail={meetup.contactEmail}
      isFavorite={meetup.isFavorite}
      on:togglefavorite />
  {/each}
</section>
