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
      controlType="text"
      id="title"
      label="Title"
      value={title}
      rows="null"
      type="text"
      on:input={event => (title = event.target.value)} />
    <TextInput
      controlType="text"
      id="subtitle"
      label="Subtitle"
      value={subtitle}
      rows="null"
      type="text"
      on:input={event => (subtitle = event.target.value)} />
    <TextInput
      controlType="text"
      id="address"
      label="Address"
      value={address}
      rows="null"
      type="text"
      on:input={event => (address = event.target.value)} />
    <TextInput
      controlType="text"
      id="imageUrl"
      label="Image Url"
      value={imageUrl}
      rows="null"
      type="text"
      on:input={event => (imageUrl = event.target.value)} />
    <TextInput
      controlType="text"
      id="contactEmail"
      label="Contact Email"
      value={contactEmail}
      rows="null"
      type="text"
      on:input={event => (contactEmail = event.target.value)} />
    <TextInput
      controlType="textarea"
      id="description"
      label="Description"
      value={description}
      rows="3"
      type="null"
      on:input={event => (description = event.target.value)} />
    <Button type="submit" caption="Save" href="" mode="" />
  </form>
  <MeetupGrid {meetups} />
</main>
