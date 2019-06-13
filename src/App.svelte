<script>
  import Header from "./UI/Header.svelte";
  import MeetupItem from "./Meetups/MeetupItem.svelte";
  import MeetupGrid from "./Meetups/MeetupGrid.svelte";
  import TextInput from "./UI/TextInput.svelte";
  import Button from "./UI/Button.svelte";

  let title = "";
  let subtitle = "";
  let imageUrl = "";
  let description = "";
  let address = "";
  let contactEmail = "";

  let meetups = [
    {
      id: "m1",
      title: "Coding Bootcamp",
      subtitle: "Learn to code in 2 hours",
      description: `In this meetup, we'll have some experts that'd teach you so much`,
      imageUrl:
        "https://cdn.workfrom.co/files/usermedia/85809-R2A1IRvER7y3IhPeURj1-IMG_7800.JPG",
      address: "Golden Mille, Medellin",
      contactEmail: "code@test.com",
      isFavorite: true
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
      contactEmail: "eat@test.com",
      isFavorite: true
    }
  ];

  function addMeetup() {
    const newMeetup = {
      id: Math.random().toString(),
      title,
      subtitle,
      description,
      imageUrl,
      address,
      contactEmail
    };
    meetups = meetups.concat(newMeetup);
  }

  function toggleFavorite(event) {
    const id = event.detail;
    console.log("ID: ", id);

    const updatedMeetup = { ...meetups.find(m => m.id === id) };
    updatedMeetup.isFavorite = !updatedMeetup.isFavorite;
    const meetupIndex = meetups.findIndex(m => m.id === id);
    const updatedMeetups = [...meetups];
    updatedMeetups[meetupIndex] = updatedMeetup;
    meetups = updatedMeetups;
  }
</script>

<style>
  main {
    margin-top: 5rem;
  }
  form {
    width: 30rem;
    max-width: 90%;
    margin: auto;
  }
</style>

<Header />

<main id="meetups">
  <form on:submit|preventDefault={addMeetup}>
    <TextInput
      id="title"
      label="Title"
      value={title}
      on:input={event => (title = event.target.value)} />
    <TextInput
      id="subtitle"
      label="Subtitle"
      value={subtitle}
      on:input={event => (subtitle = event.target.value)} />
    <TextInput
      id="address"
      label="Address"
      value={address}
      on:input={event => (address = event.target.value)} />
    <TextInput
      id="imageUrl"
      label="Image Url"
      value={imageUrl}
      on:input={event => (imageUrl = event.target.value)} />
    <TextInput
      id="contactEmail"
      label="Contact Email"
      value={contactEmail}
      type="email"
      on:input={event => (contactEmail = event.target.value)} />
    <TextInput
      controlType="textarea"
      id="description"
      label="Description"
      value={description}
      rows="3"
      type="text"
      on:input={event => (description = event.target.value)} />
    <Button type="submit" caption="Save" />
  </form>
  <MeetupGrid {meetups} on:togglefavorite={toggleFavorite} />
</main>
