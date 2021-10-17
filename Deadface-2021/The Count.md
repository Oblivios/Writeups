## The Count - *Programming*

### - Description -

>  Apparently DEADFACE is recruiting programmers, but spookyboi is a little apprehensive about recruiting amateurs.
He's placed a password hash in the form of a flag for those able to solve his challenge. Solve the challenge and submit
the flag as flag{SHA256_hash}.

> `code.deadface.io:50000`

> (We were also given a link to a thread which wasn't that useful for this challenge)

### - Solution -

I first tried to connect to the IP address, by doing `nc code.deadface.io 50000`, and I saw that it was generating random words.

So I decided to create a python script, who would connect to the IP address and the port, who would retrieve the word, and then do what the challenge asks us to do.

I imported the socket module to connect to the IP address, then received and stocking the random word, and did a basic loop to get the sum of the letters of the word.

I then sent the result and asked to receive an answer, which would give me `b'\nflag{d1c037808d23acd0dc0e3b897f344571ddce4b294e742b434888b3d9f69d9944}\n'`

Here's a picture of the code and the result:

![Code&Result](https://user-images.githubusercontent.com/68814228/137636091-946800d6-f122-4eb7-a354-8ce9becc2e21.png)
