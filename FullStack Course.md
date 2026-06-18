![][image1]

# 

# **FullStack crash course steps**

1. ## **Setup BE tech stack**

   1. Node.js Fastify server \+ TypeScript  
   2. [Drizzle ORM](https://orm.drizzle.team/)  
   3. [PostgreSQL](http://PostgreSQL)  
   4. [ZOD](https://zod.dev/) for API input/output validation  
   5. [Swagger](https://swagger.io/) for automatic documentation and typings for all endpoints.

   **Artifacts:** [Video lesson](https://drive.google.com/file/d/16bloVCcpMljFsGFGSYy3MPQMloAf2RQe/view?usp=drive_link), starter template link. [BE-boilerplate](https://github.com/DenysPoliarush/BE-boilerplate).

   **Homework:** [Homework](https://docs.google.com/document/d/10ktxl2-oT645nGz7HECIgWSGMHZCCGrzjHLSXV_kL_8/edit?tab=t.0#heading=h.y4zqbani75kx)

   

2. ## **Database & ORM: PostgreSQL, Drizzle, Migrations & CRUD**

   1. Use a Docker container locally with the required set of tools for DB Launch.  
   2. Add basic tables, relations between tables, blog posts, \<\> blog comments relations.  
   3. Understand how to make migrations to DB (using Drizzle CLI)  
   4. Add initial migration.  
   5. Add new tables \- posts and comments, update columns with migration  
   6. Add a basic CRUD for posts and comments

	**Artifacts:** [Video lesson](https://drive.google.com/file/d/1svz-p_qnew5I9WiUIjKaI5Fjgd_Qxofr/view?usp=drive_link)  
	**Homework**: [Homework](https://docs.google.com/document/d/1dLwVBRaJN3SXqyNU8Yktnt_hS9sExXXkn-0K3bAkB_4/edit?usp=drive_link)

##     2.1 **Supabase implementation**

7. Create an account on Supabase and connect to the remote DB  
   8. Create a local DB with Supabase CLI and connect to the local DB  
   9. Run migrations for both databases  
   10. Add a new field to the schema and run migration for both databases

	**Homework:** [Homework](https://docs.google.com/document/d/17etSGgAj6N0mlCeTsH9pyxod9SsFs0083GcwqYJJk9A/edit?tab=t.0#heading=h.5tcg2atnbthy)

3. **Add pagination, search functionality, and sorting to CRUD.**  
   1. Limit/offset pagination  
   2. cursor-based pagination  
   3. sorting by one or many parameters  
   4. filtering by  comments count

**Artifacts:** [Video lesson](https://drive.google.com/file/d/1EQtR1YfnP5tfA5oClAc8iBOiuk3mWWMT/view?usp=drive_link).  
**Homework**: [Homework](https://docs.google.com/document/d/1L8CcXBIvuQ0b-2Uw9t0GfN7xhFfbIT2EdN6j9EwnHQg/edit?usp=sharing)

4. **Auth System**   
   **\-Configure and set up Auth via [Supabase](https://supabase.com/)**  
   **\-Configure and set up Auth via [Amplify Cognito](https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-integrate-apps.html)(optional)**

   1. ## Register via simple email+password (confirmation email is optional).

   2. ## Login via email+password

   3. ## Implement correct server-side middleware.

   4. ## Handle correct 401responses

   5. Reset password flow  
   6. Create (fake or real) users and connect them to existing posts and comments and show them on FE.

	**Artifacts:** [Video lesson](https://drive.google.com/file/d/16k8Y9dD7CHaLZa40wcWehnO3dXcGBwjv/view?usp=sharing)(Cognito)  
	**Homework:** [Homework(Cognito)](https://docs.google.com/document/d/11jFzKLwDCD31az7Sr50U0qWBSfpgB_5UQqEyaMfvdSY/edit?tab=t.0#heading=h.cb7f7naczt8m), [Homework(Supabase)](https://docs.google.com/document/u/0/d/1FgXtG9EuAc_jtZMLnLM1DvUND1_t9B15BJ_0iez862Q/edit)

5. **Implement a role system for 2 roles: Admin / User**  
   1. Implement the **Admin** page to see all users in the system with pagination and search.   
   2. Implement a feature to deactivate a user from the **Admin** panel (Using Cognito API)

   3. ## Handle correct 403 responses and understand the difference between authentication and authorization.

**Artifacts:** [Video lesson](https://drive.google.com/file/d/1xlFQsPE_kuaZD90BfkUpO-7YHRy86qRb/view?usp=drive_link).  
**Homework:** [Homework](https://docs.google.com/document/d/1pkA5UH-W0OVS6rIP70tQABY0Cnb6hlrV8Nj2MEBXRtQ/edit?tab=t.0#heading=h.fj0aaydg34a6)

6. **Invite users from the admin panel**  
   1. Track status of invitation.  
   2. Send/resend invite functionality.  
   3. accept-invite functionality.  
   4. Connect email delivery tool, [Resend](https://resend.com/) or [Sendgrid](https://sendgrid.com/en-us) or [Loops](https://loops.so/) to send invitation emails.

	**Homework:** [Homework](https://docs.google.com/document/d/1ho3pUyH03FcSa3uyvO9ly7d6t_NDwGg31ySAoERfngg/edit?tab=t.0#heading=h.wzwpjjxht3ns)

7. **Many-to-many relations. Add tags**  
   1. Create tags management page in **Admin** dashboard  
   2. CRUD for tags   
   3. Allow users to add tag to posts during the creation or update of the post he is owner  
   4. On the posts search page, implement filters by tags (multiple) and return only correct posts.

8. **Delete functionality (soft vs hard)**  
   1. **Admin** can delete users and all user entities \- posts, my comments, and comments under posts (soft delete)  
   2. **Admin** can delete users, but make a backup of all user entities \- posts, my comments, comments under posts (hard delete)  
   3. **Admin** has a new page or tab: archived users list (from archive)  
   4. **Admin** can restore users from archives with all entities.  
   5. Understand what **transactions** in DB mean, why we need them, and how to use them. What limitation is inside the transaction code?

	Homework: [Homework](https://docs.google.com/document/d/1huCQpMxZUxRgn_yK9CvD7Nhp_ZOMy5YAyfCW-W5QJ-0/edit?tab=t.0)

9. **\* Bonus CrashCourse tasks**  
   1. Implement login via Google oAuth from cognito  
   2. Generate a PDF file from HTML using Puppeteer and download it. (Queries \+ Store signed file with expiration date).  
   3. Send events invitation via Calendars API (mimic Calendly flow).  
   4. Integrate onboarding flow for users with some async onboarding step. (Which takes time on BE to proceed).

10. **Advanced Exercise: Compare Cloud Backend Solutions**  
    1. Reimplement core functionality of the BE project using Firebase and Supabase to learn the difference and be familiar with the Cloud BE solution for such tasks.

11. **Additional Topics for Discussion**  
    1. Security best practices during backend development: secure env vars, production access, privacy topics, SQL injection attacks, DDOS.  
    2. Monitoring, profiling, and reporting of health checks, usage, and errors in [Node.js](http://Node.js). 

12. **\[Deploy\] TBA**

# **Assessment Routine**

1. FullStack assessment happens after finishing pre-assessment tasks and reviewing them. \~2 weeks after the candidate sent tasks for review.  
2. All pre-assessment tasks reviewed with scores from 0 to 10 (10 \- perfect, 8 \- good, 6 average, \<5 not good).  
3. Every assessment conducted by owner of FullStack department \- [Denys Poliarush](mailto:d.polyarush@softonix.org) and invited guests from the BE team.  
4. The first 30 minutes of the assessment are focused on pre-assessment tasks review. The owner of the FullStack department will share a screen, conduct the demo of issues/highlights he found during review, and ask questions where needed.  
5. Next part \~30-45 goes for general questions. Questions on the assessment should be focused on topics covered during course as well as a little bit beyond \- but not too much. Keep in mind \- it’s not a Backend course, it is a FullStack course. Asking about DB (relations, queries) and async specifics of [Node.js](http://Node.js) are must have.   
6. Our goal is to make sure the candidate has basic BE knowledge and is able to be a stable support for the Backend team.  
7. After completion of the assessment, the candidate will receive one of possible results: \`Perfect\`, \`Good\`, \`Not enough\` and feedback on where to focus his attention.  
8. In case of \`Good\` and \`Perfect\` results, candidates will receive a personalized bonus.  
9. The owner of the FullStack department receives a personalized bonus after entire class completion, either for 1 group or for multiple groups.

[image1]: <data:image/png;base64,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>