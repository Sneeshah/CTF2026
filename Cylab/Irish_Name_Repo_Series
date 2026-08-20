# Irish Name Repo Series


## Description:
No idea what it is about, but it is labeled a medium difficulty task.


### Irish-Name-Repo 1

#### Question: Do you think you can log us in? Try to see if you can login!


 1) site has problems with the name Conan O'Brien, prolly cause 'is sql
 2) in network tab I see debug= in the post request. but it should just be name and passwort
 3) in the html I can set debug to 1 and now I don't just get login failed but a whole message with the sql query username and password used
 4) gotta inject sql code here, anything that sets username to true and then escapes the rest with a comment work
 5) ' or '1'='1' --
 6) picoCTF{s0m3_SQL_85832275}
 7) Note: needed quite some time for this, need to brush up on sql injections and web exploits for sure.

### Irish-Name-Repo 2

#### Someone has bypassed the login before, and now it's being strengthened. Try to see if you can still login!

 1) same trick gets us the same page but this time we don't get the flag but "SQLi detected"
 2) after some tests it was obvious the injection-check was just looking for or/OR
 3) since it is an admin login we can try admin as username to get true instead (what or '1'='1' did before)
 4) admin' -- worked
 5) picoCTF{m0R3_SQL_plz_8c334129}

### Irish-Name-Repo 3

#### Try to see if you can login as admin!

 1) this time it encrypts whatever we put in admin -> nqzva
 2) just put in the whole alphabet gets us nopqrstuvwxyzabcdefghijklm
 3) so whole thing is just rot13
 4) ' or '1'='1' -- becomes ' be '1'='1' -- so it changes to or after encryption and voila
 5) picoCTF{3v3n_m0r3_SQL_2af58a67}
