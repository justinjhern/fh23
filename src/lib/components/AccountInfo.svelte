<script>
    import { goto } from "$app/navigation";
    import { isLoggedIn } from "./utils/auth";
    import { collection, doc, setDoc, getFirestore } from "firebase/firestore"; 
    import app from "./utils/fb";
  import { USERDOMAIN, USERPROFILE } from "$env/static/private";

    const db = getFirestore(app);

    let form;
    let submitter;

    /*const data = {
        uid: "",
        is_tutor: false,
        phone_number: "",
        subject: "none",
    }*/

    function handleClick() {
        
        const formdata = document.querySelector("#profile")?.;
        const formData = new FormData(form, submitter);
        await setDoc(doc(db, USERPROFILE, "profile"), {
            fname: firstname,
            lname: lastname,
            pnum: phonenumber,
    }).then(() => { }).catch((error) => {
      console.log(error);
    });
	}
</script>

  <h3>Profile</h3>

  <div>
    <form id="profile" bind:this={form}>
      <label for="fname">First Name</label>
      <input type="text" id="fname" name="firstname" placeholder="Your name..">

      <label for="lname">Last Name</label>
      <input type="text" id="lname" name="lastname" placeholder="Your last name..">

      <label for="pnum">Phone Number</label>
      <input type="text" id="pnum" name="phonenumber" placeholder="Phone number..">

      <button on:click|preventDefault={handleClick} bind:this={submitter} type="submit" id="submit">Submit</button>


    </form>
  </div>
