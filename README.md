# Linux Setup Check with Ansible

For the course Linux essentials, students get an assignment where they need to setup a freshly installed linux system.

They get a list of requirements that they have to implement on the linux system. The actual target is a Raspberry Pi but that is of no importance for this assignment.

Currently the grading happens using a bash script that checks every requirement. The problem with this script is that is hard to maintain, requires a lot of testing and needs to run on the target system.

For this assignment a demo should be created that shows of what is possible using Ansible so an evaluation can be made if Ansible is a better candidate for this kind of work.

Below you will find a list of basic requirements and descriptions of the tasks students have to accomplish. Each is accompanied with the checks that we should be able to make using Ansible. The original check script cannot be supplied because this should be kept private with the teacher.

Note that the checks are elementary in nature and are not all inclusive. This is because some requirements may be implemented partially by the student and we want to grade accordingly. Partial solutions should result in partial credits for the student.

## Basic Requirements

1. Create a new user called `student` that belongs to the groups `students`.
   1. Check if a `students` group exists
   2. Check if a `student` user exists
   3. Check if the `student` user belongs to the `students` group
2. Create a file called `my_name` in the home directory of the `student` user. Put your name inside of it in lowercase letters. Make sure that the file can only be read and written to by the `student` user.
   1. Check if the file `my_name` exists in the home directory of the user `student`
   2. Check if the file has content (maybe check if content matches list of students?)
   3. Check if the permissions on the file are correct: `600`
3. Setup apache web service and provide a personal web page with the content shown below where you replace the token `__STUDENT__`with your own name (all lowercase again).
   1. Check if apache is installed
   2. Check if the service is running
   3. Check if an HTTP request to `http://localhost` returns a valid web page (http code 200).
   4. Check if the return page contains the name of the student

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Personal WebPage</title>
</head>
<body>
  <h1>Welcome to the website of __STUDENT__</h1>  
</body>
</html>
```

4. Create an alias `distro` for the user `student` of the command `lsb_release -ds`. Make sure it is available after logging in.
   1. Check if the alias exists
   2. Check if the result of the alias is the same as the result of `lsb_release -ds`
