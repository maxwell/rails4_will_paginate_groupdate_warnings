Tracking down warnings on Rails 4

When trying to update my existing Rails 4 app, I was coming up with some weird warnings littered all over my tests, and with some Googling, some other people seemed to have it too.

https://github.com/rails/rails/issues/10507

```
/Users/maxwell/.rvm/gems/ruby-2.0.0-p247/gems/activerecord-4.0.0/lib/active_record/core.rb:103: warning: already initialized constant #<Module:0x007fbb60919038>::AttrNames
/Users/maxwell/.rvm/gems/ruby-2.0.0-p247/gems/activerecord-4.0.0/lib/active_record/core.rb:103: warning: previous definition of AttrNames was here
```

After doing some real yak shaving, I realized that it was having the combo of both the will_paginate and groupdate gems in my Gemfile.


To see the errors for yourself.

```
bundle
rake db:migrate

bundle && rails r "Post.first"

```

Then, you will see the warning

if you comment out either of the gems and re-run

```
bundle && rails r "Post.first"

```

no warnings!


Not sure of exactly WHY, but at least now I know WHO :)