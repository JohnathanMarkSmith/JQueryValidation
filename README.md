### JQueryValidation

This is just a one JSP page example that demos some JQuery Validation stuff.  Yes I really did not have to use a JSP and tomcat7 but again this is only a one page example so why not... :)

in my example I have some HTML code that looks like the following:

        <div>
            <form id="myForm">
                <p>
                    <label for="firstName">First Name:</label>
                    <input id="firstName" name="firstName"></input>
                </p>
                <p>
                    <label for="lastName">Last Name:</label>
                    <input id="lastName" name="lastName"></input>
                </p>
                <p>
                    <label for="age">Age:</label>
                    <input id="age" name="age"></input>
                </p>
                <p>
                    <input type="submit" value="Submit" />
                </p>
            </form>
        </div>

I wanted to put some validation in to check that data was entered into the fields and why not use JQuery for it..

I then made the following style sheet code:

            <style type="text/css">
                    #errorContainer {
                        display: none;
                        overflow: auto;
                        background-color: #FFDDDD;
                        border: 1px solid #FF2323;
                        padding-top: 1;
                    }

                    #errorContainer label {
                        float: none;
                        width: auto;
                    }

                    input.error {
                        border: 1px solid #FF2323;
                    }

             </style>


This is going to setup how the errors will look.  I then had to add a place on my page for the errors so I added the following div:

        <div id="errorContainer">
            <p>&nbsp;Please correct the following errors and try again:</p>
            <ul />
        </div>

### The above code is where JQuery will be displaying the errors. Now its time for the HARD work :)

You need to add the JQuery and the Validate libs into your code by added the following lines:

        <script type="text/javascript" src="http://ajax.aspnetcdn.com/ajax/jQuery/jquery-1.7.2.min.js"></script>
        <script type="text/javascript" src="http://ajax.aspnetcdn.com/ajax/jquery.validate/1.9/jquery.validate.min.js"></script>


        <script type="text/javascript">
            $(function(){

                $('#myForm').validate({
                    rules: {
                        firstName: "required",
                        lastName: "required",
                        age: {
                            required: true,
                            range: [18,70]
                        }
                    },
                    messages: {
                        firstName: "Please enter your first name.",
                        lastName: "Please enter your last name.",
                        age: {
                            required: "Please enter your age.",
                            range: "Your age must be between 18 and 70."
                        }
                    },
                    errorContainer: $('#errorContainer'),
                    errorLabelContainer: $('#errorContainer ul'),
                    wrapper: 'li'
                });

            });
        </script>

You can see how easy it is to use JQuery Validation...


### How To Get The Project and Run It

checkout the project from github.

    git clone git@github.com:JohnathanMarkSmith/JQueryValidation.git
    cd JQueryValidation
    mvn tomcat7:run

Then open http://localhost:8080/JQueryValidation/ in your browser

If you have any questions please email me at john@johnathanmarksmith.com
