# Hostel-mess-management[project 1]
This is a console-based project for engineering students to practice and learn to program. In this hostel management system project, users can enter new students, update existing students, remove existing students, view the students' list, and manage the students' payment 




#include <stdio.h>
#include <stdlib.h>

#define RATE_PER_DAY 120

struct Student {
    int roll;
    char name[30];
    int days;
    float bill;
};

int main() {
    struct Student s[100];
    int n = 0, choice, i, r, found;

    while (1) {
        printf("\n--- HOSTEL MESS MANAGEMENT SYSTEM ---\n");
        printf("1. Add Student\n");
        printf("2. Mark Attendance (Days Taken Food)\n");
        printf("3. Calculate Mess Bill\n");
        printf("4. Display All Students\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {

        case 1:
            printf("Enter Roll Number: ");
            scanf("%d", &s[n].roll);
            printf("Enter Name: ");
            scanf(" %[^\n]", s[n].name);
            s[n].days = 0;
            s[n].bill = 0;
            n++;
            printf("Student added successfully.\n");
            break;

        case 2:
            printf("Enter Roll Number: ");
            scanf("%d", &r);
            found = 0;
            for (i = 0; i < n; i++) {
                if (s[i].roll == r) {
                    printf("Enter number of days food taken: ");
                    scanf("%d", &s[i].days);
                    found = 1;
                    break;
                }
            }
            if (!found)
                printf("Student not found.\n");
            break;

        case 3:
            for (i = 0; i < n; i++) {
                s[i].bill = s[i].days * RATE_PER_DAY;
            }
            printf("Mess bill calculated successfully.\n");
            break;

        case 4:
            printf("\nRoll\tName\t\tDays\tBill\n");
            printf("------------------------------------------\n");
            for (i = 0; i < n; i++) {
                printf("%d\t%s\t%d\t%.2f\n",
                       s[i].roll, s[i].name, s[i].days, s[i].bill);
            }
            break;

        case 5:
            exit(0);

        default:
            printf("Invalid choice.\n");
        }
    }
    return 0;
}
