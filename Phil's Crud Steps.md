Phil's Crud Steps

in picker app:
`User: email`
`Photos: title, image_uri, user_id`

- 	`rails new picker -d postgresql -T`
-  cd into picker
-  `rake db:create`
-  `rails g model Photo title image_url user_id:integer`
-  `rails g model User email password_digest`
-  `rake db:migrate`
-  `rails g controller photos new index edit show`
-  `rails g controller users index new edit show`
-  `subl .`
-  `gem install bootstrap-sass` in console
-  `bundle install`
-  in application.SCSS:`@import 'bootstrap-sprockets'
@import 'bootstrap'`
- in application.html.erb: wrap YIELD in a div with container class
 
`resources :photos`
 `resources :users`
-   `rails g controller static_pages home`
-   in routes.rb:  
 `root 'static_pages#home'`
 - in home.html.erb: 

 cmnd+shift+p
 navbar
 
 `bs3`
 cmnd+shift+p `packi` `bootstrap 3`
 
 <%= link_to 'Delete', photo_path(photo),
           method: :delete,
           data: {confirm: 'Are you sure?' } %>
           
google images image size: exactly.
save photo in the (public) photo folder

link to <img src="/images/photos/<% photo.image_url