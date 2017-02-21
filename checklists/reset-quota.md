MiddCourses keeps track of two review counts, `semester_reviews` and `total_reviews`.
The number of reviews a user has to write before they can see any others is calculated as
`quota - semester_reviews`.

Usually users have to write 2 reviews per semester before they can see others (quota = 2).
However, at the beginning of a new school year, and at the beginning of spring term (beginning
of the school year for Febs), quota is set to 0, since the new students haven't taken any courses.

### Setting the quota

0. Navigate to http://www.middcourses.com/djadmin/cr_admin/adminquota/2/ and set the **New quota**
field to either 0 or 2.
0. Save the AdminQuota object

### Resetting `semester_reviews` to 0

You must do this when you change the quota from 0 to 2, or the change won't have an effect.

0. Start a Django shell in production `heroku run python manage.py shell` (you must be in the `coursereviews` directory)
0. In the shell:

```python
from users.models import UserProfile

# Sanity check. Should be some number > 0.
UserProfile.objects.filter(semester_reviews__gt=0).count()

# Actually reset the `semester_reviews` field for everyone. ⚠️This is the important part!⚠️
for u in UserProfile.objects.all():
    u.semester_reviews = 0
    u.save()

# Again, the sanity check. Shoud be 0.
UserProfile.objects.filter(semester_reviews__gt=0).count()
```
