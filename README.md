# Forward-and-Reverse-search-in-doubly-linked-list
#include <iostream>
using namespace std;
class Node
{
public:
    int data;
    Node *pre;
    Node *next;
    Node *tail;
};

void creates(Node **head, int size)
{
    *head = new Node();
    Node *temp = *head;
    cout << "Enter the value at the head:" << endl;
    cin >> temp->data;
    temp->next = NULL;

    for (int i = 0; i < size; i++)
    {
        Node *n = new Node();
        Node *pre;
        Node *tail;
        cin >> n->data;
        temp->next = n;
        n->pre = temp;
        temp = n;
        tail = n;
        cout << "THE Tail is as:" << tail->data << endl;
    }
}

bool forwardsearch(Node **head, int search)
{
    Node *temp = *head;
    while (temp != NULL)
    {
        if (temp->data == search)
        {
            return true;
        }
        temp = temp->next;
    }
    return false;
}



bool previousSearch(Node *tail)
{
    Node *temp = tail;
    int preser;
    cout << "ENter the Element you want to search previously:" << endl;
    cin >> preser;

    while (temp != NULL)
    {
        if (temp->data == preser)
        {
            return true;
        }
        temp = temp->pre;
    }
    return false;
}
void DisplayReverse(Node *head)
{
    Node *temp = head;
    while (temp->next != NULL)
    {
        temp = temp->next; // Move to the last node
    }

    cout << "Displaying in Reverse Order: ";
    while (temp != NULL)
    {
        cout << temp->data << " ";
        temp = temp->pre;
    }
    cout << endl;
}


void Display(Node *head)
{
    Node *temp;
    temp = head;
    cout << "Display the original liked list:" << endl;
    while (temp != NULL)
    {
        cout << temp->data << " ";
        temp = temp->next;
    }
}

int main()
{
    int s;
    cout << "ENter the no of nodes you want to creates:" << endl;
    cin >> s;
    Node *head = NULL;
    int op;

    do
    {
        cout << endl;
        cout << "1 to add Element in the linked list:" << endl;
        cout << "2 to Display the ELement in the linked list:" << endl;
        cout << "3 to Forward search:" << endl;
        cout << "4 to previous search:" << endl;
        cout << "0 to terminates:" << endl;
        cout << "Enter the op you want to run:" << endl;
        cin >> op;
        switch (op)

        {
        case 1:
            creates(&head, s);
            break;

        case 2:
            Display(head);
            break;

        case 3:
            int sear;
            cout << "Enter the element you want to search:" << endl;
            cin >> sear;
            if (forwardsearch(&head, sear))
            {
                cout << "The Element is found:" << sear << endl;
            }
            else
            {
                cout << "The Element is not found:" << endl;
            }
            cout<<"Display forward is as:"<<endl;
            Display(head);
            break;

        case 4:
            if (previousSearch(head))
            {
                cout << "The Element is found in reverse:" << endl;
            }
            else
            {
                cout << "Not found:" << endl;
            }
            cout<<"Displaying the previous is as:"<<endl;
            DisplayReverse(head);
            break;
        }
    } while (op != 0);
}
