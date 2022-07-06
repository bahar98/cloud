# cloud


chosen project: https://github.com/OmerFI/PyForum

Services: user, post, comment

Reasons for choosing these services: 1. user service because in this service we can create the jwt token that is required. 2. post service because in this service we will be communicating with both other services and aside from communication with the user service, in communication with the comment service we will be able to use gRPC calls which is one of the requirements of this phase. 3. This service, comment has been chosen because of very similiar reasons that the post service has been chosen, as well as the fact that post and comment services should be seperate entities so that they can be developed individually.

Portion of code for user service: 
    
    https://github.com/OmerFI/PyForum/blob/main/backend/base/models.py : lines 13-15 
    https://github.com/OmerFI/PyForum/blob/main/backend/api/serializers.py : lines 8-36
    https://github.com/OmerFI/PyForum/blob/main/backend/api/urls.py : line 11 & 41-42
    https://github.com/OmerFI/PyForum/blob/main/backend/api/views.py : lines 32-40
    https://github.com/OmerFI/PyForum/blob/main/backend/backend/settings.py : lines 89-127
    https://github.com/OmerFI/PyForum/blob/main/backend/base/migrations/0001_initial.py : lines 22-47 (database structure)
    https://github.com/OmerFI/PyForum/blob/main/backend/base/migrations/0007_alter_user_email.py : lines 13-17
    https://github.com/OmerFI/PyForum/blob/main/backend/base/admin.py : lines 33-40
    

Portion of code for post service: 

    https://github.com/OmerFI/PyForum/blob/main/backend/base/models.py : lines 57-72
    https://github.com/OmerFI/PyForum/blob/main/backend/api/serializers.py : lines 83-99
    https://github.com/OmerFI/PyForum/blob/main/backend/api/urls.py : line 36
    https://github.com/OmerFI/PyForum/blob/main/backend/api/views.py : lines 110-156
    https://github.com/OmerFI/PyForum/blob/main/backend/base/migrations/0001_initial.py : lines 90-101 (database structure)
    https://github.com/OmerFI/PyForum/blob/main/backend/base/migrations/0004_alter_post_options_profile_posts.py : lines 13-16
    https://github.com/OmerFI/PyForum/blob/main/backend/base/migrations/0008_alter_comment_content_alter_post_content_and_more.py : lines 19-23
    https://github.com/OmerFI/PyForum/blob/main/backend/base/migrations/0009_alter_post_title.py : lines 14-18
    https://github.com/OmerFI/PyForum/blob/main/backend/base/admin.py : lines 14-18 & 43

Portion of code for comment service:

    https://github.com/OmerFI/PyForum/blob/main/backend/base/models.py : lines 45-54
    https://github.com/OmerFI/PyForum/blob/main/backend/api/serializers.py : lines 102-127
    https://github.com/OmerFI/PyForum/blob/main/backend/api/urls.py : lines 37-39
    https://github.com/OmerFI/PyForum/blob/main/backend/api/views.py : lines 159-199
    https://github.com/OmerFI/PyForum/blob/main/backend/base/migrations/0001_initial.py : lines 58-66 (database structure)
    https://github.com/OmerFI/PyForum/blob/main/backend/base/migrations/0008_alter_comment_content_alter_post_content_and_more.py : lines 14-18
    https://github.com/OmerFI/PyForum/blob/main/backend/base/admin.py : lines 7-11 & 44
    
     
(Parts of the code that are about category, reply and profile are overlooked to keep the project simple and lightweight. Other parts are needed in all of the services.)


![Untitled drawing](https://user-images.githubusercontent.com/74864000/177577917-eefdf7b2-b556-43d4-b27f-4b890d1de3be.jpg)

![Untitled drawing(1)](https://user-images.githubusercontent.com/74864000/177585081-e630ebc6-4d3c-4f3b-a093-e7b35c7d0a7e.jpg)



Dependencies: 

course-service --> user-management-service:
        where: monolith/users/models.py, class: User
        happened: monolith/courses/views.py, class: CourseView
        code: Users.objects.get(id=student_id)
        reason: must obtain user from database
        solution: trust user_id from jwt token
