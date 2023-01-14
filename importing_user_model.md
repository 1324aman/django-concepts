## get_user_model() or settings.AUTH_USER_MODEL

They both have different use cases.

1. settings.AUTH_USER_MODEL returns a string.<br>
settings.AUTH_USER_MODEL when you need to referencing User model in ForeignKey, ManyToManyField or OneToOneField. E.g.
```
class MyModel(models.Model):
 user = models.ForeignKey(settings.AUTH_USER_MODEL)
``` 
 
2. get_user_model() returns class name i.e, User<br>
It is used when we are writing any query for user model. <br>
Instead of referring to User directly, you should reference the user model using django.contrib.auth.get_user_model(). This method will return the currently active user model – the custom user model if one is specified, or User otherwise.

### 3. If you reference User directly (for example, by referring to it in a foreign key), your code will not work in projects where the AUTH_USER_MODEL setting has been changed to a different user model. Therefore get_user_model() should be used.
