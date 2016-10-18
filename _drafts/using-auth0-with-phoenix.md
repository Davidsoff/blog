---
layout: post
title: Using Auth0 with phoenix
---

I am currently learning about Elixir, OTP and Phoenix. So when the time came to start a new project I made the decision to use Phoenix. The application is reasonably simple but it does need some kind of authentication and authorisation. 
Because authentication is a problem that has been solved a milion times over and is something that has a huge impact when messed up, I decided to go with Auth0 for my authentication.

~~~ elixir
scope "/auth", ReadingList do
	pipe_through :browser

	get "/:provider", AuthController, :request
	get "/:provider/callback", AuthController, :callback
end

scope "/app", ReadingList do
	pipe_through :browser

	get "/", HomeController, :index, as: :home
end
~~~
