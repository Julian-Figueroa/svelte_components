<script>
  import Header from "./UI/Header.svelte";
  import MeetupItem from "./Meetups/MeetupItem.svelte";

  const meetups = [
    {
      id: "m1",
      title: "Coding Bootcamp",
      subtitle: "Learn to code in 2 hours",
      description: `In this meetup, we'll have some experts that'd teach you so much`,
      imageUrl:
        "https://cdn.workfrom.co/files/usermedia/85809-R2A1IRvER7y3IhPeURj1-IMG_7800.JPG",
      address: "Golden Mille, Medellin",
      contactEmail: "code@test.com"
    },
    {
      id: "m2",
      title: "Let's go for eat",
      subtitle: "Eat all that you want",
      description:
        "In this meetup, we'll have some experts that'd judge your eating skills",
      imageUrl:
        "https://upload.wikimedia.org/wikipedia/commons/3/3c/Wikimedia_Australia_meetup_Melbourne.jpg",
      address: "Melbourne Park, Australia",
      contactEmail: "eat@test.com"
    }
  ];
</script>

<style>
  #meetups {
    margin-top: 5rem;
  }
</style>

<Header />

<section id="meetups">
  {#each meetups as meetup, i (meetup.id)}
    <MeetupItem />
  {/each}
</section>
