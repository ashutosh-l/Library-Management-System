# Library-Management-System

                                                     Library Management System
Ashutosh
 
Problem statement :   Create  a dynamic web page for the Library  Management System 
With 2 role (Librarian and Admin) 

                                                                              Workflow Explanation: 
  HTML Form Submission: 
      The process starts when a user submits an HTML form to request a book or  to remove a student  etc . 
      The form data includes information such as student ID, book ID, or student ID to be removed. 
  Servlet Handling: 
      Upon form submission, the servlet (BookRequestServlet ,  RemoveStudentServlet  etc) intercepts the request. 
      It extracts the relevant data from the request parameters (e.g., student ID, book ID). 
      The servlet then interacts with the LibraryManagementSystem class to perform the requested action (e.g., borrowing a book, removing a student). 
  Database Interaction: 
      The LibraryManagementSystem class interacts with the database to perform operations like borrowing a book , removing a student, adding a student. 
      It executes SQL queries to insert, update, or delete records in the database tables (students, books, etc.). 
      The LibraryManagementSystem class handles database connections, queries, and exception handling. 
  Error Handling: 
      If any errors occur during database operations (e.g., SQLException), they are caught by the servlet. 
      The servlet then sends an appropriate response to the client, either displaying an error message or logging the error for debugging. 
 
 
                                                                          User Roles and Functions 
    Admin Role 
      Add Student: Adds new student records to the database. 
          HTML Form: Add_student.html 
          Servlet: AddStudentServlet.java 
      Add Book: Allows entry of new books into the database. 
          HTML Form: Add_book.html 
          Servlet: AddBookServlet.java 
      Block/Unblock Student: Changes the status of a student's account. 
          HTML Form: Block.html 
          Servlet: SetStudentActiveStatusServlet.java 
      Generate PDF: Triggers the creation of a PDF report. 
          HTML Button: pdf_generation.html 
          Servlet: BookReportServlet.java 
      View Defaulter: Lists students with overdue books. 
          HTML Page: defaulter.html 
          Servlet: OverdueBooksServlet.java 
      Change Password: Allows users to change their passwords. 
          JSP: password_changed.jsp 
          Servlet: ChangePasswordServlet.java 
      Remove Student: Removes a student's record from database. 
          HTML Form: remove_student.html 
          Servlet: RemoveStudentServlet.java 
      Modify Student Details: Updates student information. 
          HTML Form: modify_student.html 
          Servlet: ModifyStudentServlet.java 
     
    Librarian Role 
      Renew Book: Renews a book . 
          HTML Form: renew.html 
          Servlet: BookRenewServlet.java 
      Search Book: Searches the book . 
          HTML Form: search.html 
          Servlet: SearchBookServlet.java 
      Available Book: Views books available for borrow. 
          HTML List: available_books.html 
          Servlet: AvailableBooksServlet.java 
      Check Book Status: Checks the availability of a book. 
          HTML Form: check_book_status.html 
          Servlet: CheckBookStatusServlet.java 

          
    Student Role 
      Request Book: Requests a book for borrow. 
          HTML Form: request.html 
          Servlet: RequestBookServlet.java 
      Return Book: Processes the return of a borrowed book. 
          HTML Form: return.html 
          Servlet: ReturnBookServlet.java 
     
 
                                                                                  Web Page Entry Points 
        Index.jsp: Serves as the entry page for users to log in. 
        Admin.html: Directs to admin-specific functions and operations. 
        Librarian.html: Leads to librarian-specific features and system management. 
        Student.html: Allows students to access features like book requests and returns. 
 
                                                                                   Admin

Admin: This is a user role within the system. An admin likely has permissions to manage the system, including managing books, students, and librarian accounts. 

Add Student: An admin function to add new student records to the system. This would correspond to an HTML form(Add_student.html) for entering student details and a Java servlet(AddStudentServlet.java) that processes this information and updates the database(students) and even in the students_passwords(by default the password is “password” and the role is “Student” stuedent need to change the password after recieving student id by the librarian). 

Add Book: Similar to adding a student, this admin function would allow the entry of new books into the system. The HTML(Add_book.java) and Java servlet(AddBookServlet.java) would operate similarly, updating the book inventory database(student_books(new coloums added with studentId, BookId with the renewal =0),books(borrowed=0)).

Block/Unblock Student: An admin function to change the status of a student's account. The HTML(block.html) for this might be a form where an admin enters a student ID, and the associated Java servlet(SetStudentActiveStatusServlet.java) would handle the request to update the student's status(student table isActive coloumns). 

Generate PDF: This likely refers to a report generation feature, where an admin can trigger the creation of a PDF document. The HTML(pdf_generation.html) could be a simple button, and the Java servlet(BookReportServlet.java) would handle the data aggregation and PDF creation. 
View Defaulter: This function allows the admin to view a list of students who have overdue books. The HTMLdefaulter.html) would likely be a page with a list or table, and the Java servlet(OverdueBookServlet.java) would query the database if the user didn’t return the book after the 45 days is in the defaulter list. 

Change Password: This could be a common function for all users to change their passwords. The JSP(password_changed.jsp) would be a form for password input, and the Java servlet(ChangePasswordServlet.java) would process the password change in the students_password table. 

Remove Student: This admin function would remove a student's record. The HTML(remove.html)  have a form to specify  student id, and the servlet(RemoveStudentServlet.java) would handle the deletion from the student table and from the student_password table (until and unless this student doesn’t have any book with him)

Modify Student Details: This function allows an admin to update student name. The HTML(modify_student.html) would include a form to input the studentID, and the servlet(ModifyStudentServlet.java)  process the updates in the student. 
 

                                                                                  Librarian

                                                                                  
Librarian: Another user role with its specific set of permissions, potentially including managing book and see the available . 

Renew: A librarian or student function to renew a book . The HTML(renew.html)  be a form to input book ID and student ID, and the servlet(BookRenewServlet.java) would update the renewal coloumnss from the student_book table in the database. 

Search: A common feature for all users to search the book from id,title or author of the book. The HTML(search.html) would have a search form, and the servlet(SearchBookServlet.java) would return the search results. 

Available Book: A librarian function to view books currently available for borrow for the student. The HTML(available_books.html) would show a list, and the servlet(AvailableBookServlet.java) would fetch the data from the books table from the database where coloumn borrowed=0. 

Check Status: This allow users to check the status of a book, such as whether it's available or borrowed by some student. The HTML(Check_book_status.html) would likely have a form to enter a book ID, and the servlet(CheckBookStatusServlet.java) would retrieve the status by checking the book table .  
Librarian.html 


                                                                                                  Student
Student: This is a user role. Students likely have access the student section like request book and return book and change the student password 

Request Book: A student feature to request a  book from the books table in the database. This would require a form in HTML(request.html) and a servlet(RequestBookServlet.java) to handle the request and after the Successfull submission the book is borrowed to that student and data is updated in the student_book table and the book table(borrowed=1). 

Return Book: This function would be used by a student to process book returns. HTML(return.html) would provide a form to record the return, and the servlet(ReturnBookServlet.java) would update the database. And after successfull submisson the book(borrowed=0) table and the student_books table  
 
 
 
