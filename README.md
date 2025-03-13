#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// Variable to keep track of the number of students
int i = 0;

// Structure to store the student
struct sinfo {
    char fname[50];
    char lname[50];
    int roll;
    float cgpa;
    int cid[10];
} st[55];

// Function to add the student
void add_student() {
    printf("Add the Students Details\n");
    printf("Enter the first name of student\n");
    scanf("%s", st[i].fname);
    printf("Enter the last name of student\n");
    scanf("%s", st[i].lname);
    printf("Enter the Roll Number\n");
    scanf("%d", &st[i].roll);
    printf("Enter the CGPA you obtained\n");
    scanf("%f", &st[i].cgpa);
    printf("Enter the course ID of each course (5 courses)\n");
    for (int j = 0; j < 5; j++) {
        scanf("%d", &st[i].cid[j]);
    }
    i++;
}

// Function to find the student by the roll number
void find_rl() {
    int x;
    printf("Enter the Roll Number of the student\n");
    scanf("%d", &x);
    for (int j = 0; j < i; j++) {
        if (x == st[j].roll) {
            printf("The Students Details are\n");
            printf("The First name is %s\n", st[j].fname);
            printf("The Last name is %s\n", st[j].lname);
            printf("The CGPA is %f\n", st[j].cgpa);
            printf("The course IDs are: ");
            for (int k = 0; k < 5; k++) {
                printf("%d ", st[j].cid[k]);
            }
            printf("\n");
            return;
        }
    }
    printf("Student with Roll Number %d not found.\n", x);
}

// Function to find the student by the first name
void find_fn() {
    char a[50];
    printf("Enter the First Name of the student\n");
    scanf("%s", a);
    int found = 0;

    for (int j = 0; j < i; j++) {
        if (!strcmp(st[j].fname, a)) {
            printf("The Students Details are\n");
            printf("The First name is %s\n", st[j].fname);
            printf("The Last name is %s\n", st[j].lname);
            printf("The Roll Number is %d\n", st[j].roll);
            printf("The CGPA is %f\n", st[j].cgpa);
            printf("The course IDs are: ");
            for (int k = 0; k < 5; k++) {
                printf("%d ", st[j].cid[k]);
            }
            printf("\n");
            found = 1;
        }
    }
    if (!found) {
        printf("The First Name not Found\n");
    }
}

// Function to find the students enrolled in a particular course
void find_c() {
    int id;
    printf("Enter the course ID\n");
    scanf("%d", &id);
    int found = 0;

    for (int j = 0; j < i; j++) {
        for (int d = 0; d < 5; d++) {
            if (id == st[j].cid[d]) {
                printf("The Students Details are\n");
                printf("The First name is %s\n", st[j].fname);
                printf("The Last name is %s\n", st[j].lname);
                printf("The Roll Number is %d\n", st[j].roll);
                printf("The CGPA is %f\n", st[j].cgpa);
                found = 1;
                break;
            }
        }
    }
    if (!found) {
        printf("No students found for Course ID %d\n", id);
    }
}

// Function to print the total number of students
void tot_s() {
    printf("The total number of Students is %d\n", i);
    printf("You can have a max of 55 students\n");
    printf("You can have %d more students\n", 55 - i);
}

// Function to delete a student by the roll number
void del_s() {
    int a;
    printf("Enter the Roll Number which you want to delete\n");
    scanf("%d", &a);
    for (int j = 0; j < i; j++) {
        if (a == st[j].roll) {
            for (int k = j; k < i - 1; k++) {
                st[k] = st[k + 1];
            }
            i--;
            printf("The Roll Number is removed Successfully\n");
            return;
        }
    }
    printf("Student with Roll Number %d not found.\n", a);
}

// Function to update a student's data
void up_s() {
    int x;
    printf("Enter the roll number to update the entry: ");
    scanf("%d", &x);
    for (int j = 0; j < i; j++) {
        if (st[j].roll == x) {
            printf("1. First name\n2. Last name\n3. Roll no.\n4. CGPA\n5. Courses\n");
            int z;
            scanf("%d", &z);
            switch (z) {
                case 1:
                    printf("Enter the new first name: \n");
                    scanf("%s", st[j].fname);
                    break;
                case 2:
                    printf("Enter the new last name: \n");
                    scanf("%s", st[j].lname);
                    break;
                case 3:
                    printf("Enter the new roll number: \n");
                    scanf("%d", &st[j].roll);
                    break;
                case 4:
                    printf("Enter the new CGPA: \n");
                    scanf("%f", &st[j].cgpa);
                    break;
                case 5:
                    printf("Enter the new courses (5 courses): \n");
                    for (int k = 0; k < 5; k++) {
                        scanf("%d", &st[j].cid[k]);
                    }
                    break;
                default:
                    printf("Invalid choice.\n");
                    return;
            }
            printf("UPDATED SUCCESSFULLY.\n");
            return;
        }
    }
    printf("Student with Roll Number %d not found.\n", x);
}

// Driver code
int main() {
    int choice;
    while (1) {
        printf("The Task that you want to perform\n");
        printf("1. Add the Student Details\n");
        printf("2. Find the Student Details by Roll Number\n");
        printf("3. Find the Student Details by First Name\n");
        printf("4. Find the Student Details by Course Id\n");
        printf("5. Find the Total number of Students\n");
        printf("6. Delete the Students Details by Roll Number\n");
        printf("7. Update the Students Details by Roll Number\n");
        printf("8. To Exit\n");
        printf("Enter your choice to find the task\n");
        scanf("%d", &choice);
        switch (choice) {
            case 1:
                add_student();
                break;
            case 2:
                find_rl ();
                break;
            case 3:
                find_fn();
                break;
            case 4:
                find_c();
                break;
            case 5:
                tot_s();
                break;
            case 6:
                del_s();
                break;
            case 7:
                up_s();
                break;
            case 8:
                exit(0);
                break;
            default:
                printf("Invalid choice. Please try again.\n");
        }
    }
}
