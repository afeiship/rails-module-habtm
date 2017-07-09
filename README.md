# rails-module-habtm
> Rails module association HABTM.

## step to step:
+ create the models:
```bash
rails g model Author name:string
rails g model Book title:string
rails g migration CreateJoinTableAuthorsBooks authors books
```
+ HABTM association in our models like this:
```rb
class Book < ApplicationRecord
  has_and_belongs_to_many :authors
end

class Author < ApplicationRecord
  has_and_belongs_to_many :books
end
```

+ we can create our database tables by running
```bash
rake db:migrate
```

+ seed codes:
```rb
herman = Author.create name: 'Herman Melville'
moby = Book.create title: 'Moby Dick'
herman.books << moby


moby.authors
herman.books
herman.books.where(title: 'Moby Dick')
```