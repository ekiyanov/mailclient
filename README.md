## Mailer client

Wrapper around gomail to send template based emails. Sender is specified with env vars:

	  MAIL_USERNAME | example@gmail.com
	  MAIL_PASSWORD | yourpassword
	  MAIL_HOST | smtp.google.com
	  MAIL_PORT | default 587
	  MAIL_FROM | Your Friend <example@gmail.com>  | Used as message Header From


Templates are compiled upon demand and cached inside simpel map. 

Lookup for templates are performed from `/templates/{TEMPLATE_NAME}`


### Usage example

    import "github.com/ekiyanov/mailclient"

    ...

    mailclient.Send("destination@gmail.com", "hello from mailclient", "welcome.html", map[string]interface{}{"var1": "param1"}) 

	// or

	mc:=mailclient.NewMailClient()
	mc.Send("destination@gmail.com", "hello", "welcome.html", map[string]interface{}{"var1": "param1"})

    ...
    
	----

	/templates/welcome.html

    <h1> Hello {{.var1}} </h1>
