<script>

    import emailjs from 'emailjs-com';
    export let activeGearItem

    import{ init } from 'emailjs-com';
    init("user_Mwx2wKXM9KCrpglLhd9cO");

    function submitForm(e) {
        e.preventDefault();
        beforeSendForm = true;
        emailjs.sendForm('service_mhmeibt', 'contact', e.target)
        .then(function(response) {
            success = true;
            window.alert("This was a triumph");
        }, function(error) {
            failure = true;
            window.alert("This was not a triumph");
        })
    }

</script>

<h4>Please ensure that the correct option is chosen in the automatic/manual selector above before clicking send on the contact form. This will ensure that your message gets to the correct team.</h4>

<div class="container">
<div class="contact-form-container" class:A={activeGearItem === "Automatic"} class:M={activeGearItem === "Manual"} on:click={() => ""}>
    <form id="contact-form" on:submit={submitForm}>
        <label for="name">Name</label>
        <input id="name" type="text" name="name">
        <label for="email">Email</label>
        <input id="email" type="email" name="email">                
        <label for="number">Contact Number</label>
        <input id="number" type="tel" name="number">
        <label for="message">Message</label>
        <input id="message" name="message">
        <input type="hidden" id="gearbox" name="gearbox" value={activeGearItem}>
        <label for="submit-button"></label>
        <input id="submit-button" type="submit" value="Send">
    </form>
</div>
</div>

<style>

    .M {
        box-shadow: 3px 3px 3px 3px #981E32;
    }

    .A {
        box-shadow: 3px 3px 3px 3px #2e75b6;
    }

    label {
        text-align: center;
    }

    input {
        width: 600px;
        border-radius: 10px;
        display:flex;
        justify-content: center;
        padding-top: 0;
        padding-left: 0;
        line-height: 1em;
    }

    h4 {
        text-align: center;
    }

    #submit-button {
        width: 250px;
        border-radius: 10px;
        justify-content: center;
    }

    .container {
        display: flex;
        justify-content: center;
        z-index: 1000;
        padding-top: 10px;
    }

    form {
        justify-content: center;
    }

    .contact-form-container {
        z-index: 1001;
        background-color: white;
        border-radius: 10px;
        border: 2px solid black;
        padding: 10px;
        display: flex;
        justify-content: center;
        align-items: center;
        width: 600px;
        position: fixed;
    }

    #message {
        height: 200px;
    }

    @media (max-width: 900px) {
        .contact-form-container {
            width: 300px;
        }
        input {
            width: 280px;
        }

        #submit-button {
            width: 280px;
        }
    }

</style>