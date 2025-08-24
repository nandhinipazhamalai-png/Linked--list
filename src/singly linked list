#include <stdio.h>
#include <stdlib.h>
#include <string.h>

struct Submission {
    int studentID;
    char assignmentTitle[50];
    char submissionDate[15];
    char status[15];
    struct Submission* next;
};

struct Submission* head = NULL;

struct Submission* createNode(int id, char* title, char* date, char* status) {
    struct Submission* newNode = (struct Submission*)malloc(sizeof(struct Submission));
    newNode->studentID = id;
    strcpy(newNode->assignmentTitle, title);
    strcpy(newNode->submissionDate, date);
    strcpy(newNode->status, status);
    newNode->next = NULL;
    return newNode;
}

void addSubmission(int id, char* title, char* date, char* status) {
    struct Submission* newNode = createNode(id, title, date, status);
    if (head == NULL) {
        head = newNode;
    } else {
        struct Submission* temp = head;
        while (temp->next != NULL) {
            temp = temp->next;
        }
        temp->next = newNode;
    }
    printf("Submission record added successfully!\n");
}

void updateStatus(int id, char* newStatus) {
    struct Submission* temp = head;
    while (temp != NULL) {
        if (temp->studentID == id) {
            strcpy(temp->status, newStatus);
            printf("Status updated successfully!\n");
            return;
        }
        temp = temp->next;
    }
    printf("Record not found for Student ID %d.\n", id);
}

void searchSubmission(int id) {
    struct Submission* temp = head;
    while (temp != NULL) {
        if (temp->studentID == id) {
            printf("\n--- Submission Found ---\n");
            printf("Student ID: %d\n", temp->studentID);
            printf("Assignment Title: %s\n", temp->assignmentTitle);
            printf("Submission Date: %s\n", temp->submissionDate);
            printf("Status: %s\n", temp->status);
            return;
        }
        temp = temp->next;
    }
    printf("No record found for Student ID %d.\n", id);
}

void displayAll() {
    struct Submission* temp = head;
    if (temp == NULL) {
        printf("No submission records available.\n");
        return;
    }
    printf("\n--- All Submission Records ---\n");
    while (temp != NULL) {
        printf("Student ID: %d\n", temp->studentID);
        printf("Assignment Title: %s\n", temp->assignmentTitle);
        printf("Submission Date: %s\n", temp->submissionDate);
        printf("Status: %s\n\n", temp->status);
        temp = temp->next;
    }
}

int main() {
    int choice, id;
    char title[50], date[15], status[15];

    while (1) {
        printf("\n--- Student Assignment Submission Tracker ---\n");
        printf("1. Add Submission\n");
        printf("2. Update Status\n");
        printf("3. Search by Student ID\n");
        printf("4. Display All Records\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);
        getchar();

        switch (choice) {
            case 1:
                printf("Enter Student ID: ");
                scanf("%d", &id);
                getchar();
                printf("Enter Assignment Title: ");
                fgets(title, sizeof(title), stdin);
                title[strcspn(title, "\n")] = '\0';
                printf("Enter Submission Date (DD/MM/YYYY): ");
                scanf("%s", date);
                printf("Enter Status (Submitted/Pending): ");
                scanf("%s", status);
                addSubmission(id, title, date, status);
                break;

            case 2:
                printf("Enter Student ID to update: ");
                scanf("%d", &id);
                printf("Enter New Status: ");
                scanf("%s", status);
                updateStatus(id, status);
                break;

            case 3:
                printf("Enter Student ID to search: ");
                scanf("%d", &id);
                searchSubmission(id);
                break;

            case 4:
                displayAll();
                break;

            case 5:
                printf("Exiting program.\n");
                exit(0);

            default:
                printf("Invalid choice! Try again.\n");
        }
    }
    return 0;
}
