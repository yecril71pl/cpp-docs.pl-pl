---
title: Wskaźników (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declarators, pointers
- declarations, pointers
- pointers [C++]
- pointers, declarations
ms.assetid: 595387c5-8e58-4670-848f-344c7caf985e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dad1f9a223d8eb97c8e59e955bd5358b27dafd08
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947859"
---
# <a name="pointers-c"></a>Wskaźników (C++)
Wskaźniki zadeklarowane za pomocą następującej sekwencji.  
  
```  
[storage-class-specifiers] [cv-qualifiers] type-specifiers   
[ms-modifier] declarator ;  
```  
  
 gdzie wszelkie deklaratora nieprawidłowy wskaźnik mogą być używane do `declarator`.  Składnia deklaratora wskaźnika prostego jest następująca:  
  
```  
* [cv-qualifiers] identifier [= expression]  
```  
  
 1. Specyfikatory deklaracji:  
  
    - Specyfikator klasy magazynowania opcjonalne. Aby uzyskać więcej informacji, zobacz [specyfikatory](../cpp/specifiers.md).  
  
    - Opcjonalny **const** lub **volatile** — słowo kluczowe zastosowania do typu obiektu, który ma być wskazywany.  
  
    - Specyfikator typu: Nazwa typu reprezentujący typ obiektu do będzie wskazywał na.  
  
 2. Specyfikator:  
  
    - Opcjonalny modyfikator właściwy dla Microsoft. Aby uzyskać więcej informacji, zobacz [Modyfikatory specyficzne dla Microsoft](../cpp/microsoft-specific-modifiers.md).  
  
    - Operator `*`.  
  
    - Opcjonalny **const** lub **volatile** — słowo kluczowe zastosowania do wskaźnika jako takiego.  
  
    - Identyfikator.  
  
    - Opcjonalny inicjator.  
  
     Deklaratora dla wskaźnika do funkcji wygląda następująco:  
  
```  
(* [cv-qualifiers] identifier )( argument-list ) [cv-qualifers]  
[exception specification] [= expression];  
```  
  
-   W przypadku tablicy wskaźników składnia wygląda następująco:  
  
```  
* identifier [ [ constant-expression ] ]  
```  
  
-   Wiele deklaratorów i ich inicjatory mogą występować razem w jednej deklaracji w rozdzielana przecinkami lista następujące Specyfikator deklaracji.  
  
 Prosty przykład deklarację wskaźnika jest:  
  
```cpp 
char *pch;  
```  
  
 Poprzedzająca deklaracja określa, że `pch` wskazuje na obiekt typu **char**.  
  
 Jest bardziej złożonym przykładem  
  
```cpp 
static unsigned int * const ptr;  
```  
  
 Poprzedzająca deklaracja określa, że `ptr` jest stały wskaźnik do obiektu typu **niepodpisane** **int** ze statycznym okresem magazynu.  
  
 W kolejnym przykładzie pokazano, jak wiele wskaźniki są deklarowane i inicjowane:  
  
```cpp 
static int *p = &i, *q = &j;  
```  
  
 W powyższym przykładzie p wskaźników i q wskaż obiektów typu **int** i są inicjowane na adresy i oraz j odpowiednio.  Specyfikator klasy magazynu **statyczne** ma zastosowanie do obu wskaźników.  
  
## <a name="example"></a>Przykład  
  
```cpp 
// pointer.cpp  
// compile with: /EHsc  
#include <iostream>  
int main() {  
   int i = 1, j = 2; // local variables on the stack  
   int *p;  
  
   // a pointer may be assigned to "point to" the value of  
   // another variable using the & (address of) operator  
   p = & j;   
  
   // since j was on the stack, this address will be somewhere  
   // on the stack.  Pointers are printed in hex format using  
   // %p and conventionally marked with 0x.    
   printf_s("0x%p\n",  p);  
  
   // The * (indirection operator) can be read as "the value  
   // pointed to by".  
   // Since p is pointing to j, this should print "2"  
   printf_s("0x%p %d\n",  p, *p);  
  
   // changing j will change the result of the indirection  
   // operator on p.  
   j = 7;  
   printf_s("0x%p %d\n",  p, *p );  
  
   // The value of j can also be changed through the pointer  
   // by making an assignment to the dereferenced pointer  
   *p = 10;  
   printf_s("j is %d\n", j); // j is now 10  
  
   // allocate memory on the heap for an integer,  
   // initialize to 5  
   p = new int(5);  
  
   // print the pointer and the object pointed to  
   // the address will be somewhere on the heap  
   printf_s("0x%p %d\n",  p, *p);  
  
   // free the memory pointed to by p  
   delete p;  
  
   // At this point, dereferencing p with *p would trigger  
   // a runtime access violation.  
  
   // Pointer arithmetic may be done with an array declared  
   // on the stack or allocated on the heap with new.  
   // The increment operator takes into account the size   
   // of the objects pointed to.  
   p = new int[5];  
   for (i = 0; i < 5; i++, p++) {  
      *p = i * 10;  
      printf_s("0x%p %d\n", p, *p);  
   }  
  
   // A common expression seen is dereferencing in combination  
   // with increment or decrement operators, as shown here.  
   // The indirection operator * takes precedence over the   
   // increment operator ++.   
   // These are particularly useful in manipulating char arrays.  
   char s1[4] = "cat";  
   char s2[4] = "dog";  
   char* p1 = s1;  
   char* p2 = s2;  
  
   // the following is a string copy operation  
   while (*p1++ = *p2++);  
  
   // s2 was copied into s1, so now they are both equal to "dog"  
   printf_s("%s %s", s1, s2);  
}  
```  
  
```Output  
0x0012FEC8  
0x0012FEC8 2  
0x0012FEC8 7  
j is 10  
0x00320850 5  
0x00320850 0  
0x00320854 10  
0x00320858 20  
0x0032085C 30  
0x00320860 40  
dog dog  
```  
  
## <a name="example"></a>Przykład  
 Inny przykład ilustruje użycie wskaźniki w strukturach danych; w tym przypadku połączonej listy.  
  
```cpp 
// pointer_linkedlist.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
struct NewNode {  
   NewNode() : node(0){}  
   int i;  
   NewNode * node;  
};  
  
void WalkList(NewNode * ptr) {  
   if (ptr != 0) {  
      int i = 1;  
      while (ptr->node != 0 ) {  
         cout << "node " << i++ << " = " << ptr->i << endl;  
         ptr = ptr->node;  
      }  
      cout << "node " << i++ << " = " << ptr->i << endl;  
   }  
}  
  
void AddNode(NewNode ** ptr) {  
   NewNode * walker = 0;  
   NewNode * MyNewNode = new NewNode;  
   cout << "enter a number: " << endl;  
   cin >> MyNewNode->i;  
  
   if (*ptr == 0)  
      *ptr = MyNewNode;  
   else  {  
      walker = *ptr;  
      while (walker->node != 0)  
         walker = walker->node;  
  
      walker->node = MyNewNode;  
   }  
}  
  
int main() {  
   char ans = ' ';  
   NewNode * ptr = 0;  
   do {  
      cout << "a (add node)  d (display list)  q (quit)" << endl;  
      cin >> ans;  
      switch (ans) {  
      case 'a':  
         AddNode(&ptr);  
         break;  
      case 'd':  
         WalkList(ptr);  
         break;  
      }  
   } while (ans != 'q');  
}  
```  
  
```Output  
  
      a  
45  
d  
a  
789  
d  
qa (add node)  d (display list)  q (quit)  
enter a number:   
a (add node)  d (display list)  q (quit)  
node 1 = 45  
a (add node)  d (display list)  q (quit)  
enter a number:   
a (add node)  d (display list)  q (quit)  
node 1 = 45  
node 2 = 789  
a (add node)  d (display list)  q (quit)  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Operator bezpośredni: *](../cpp/indirection-operator-star.md)   
 [Operator Address-of: &](../cpp/address-of-operator-amp.md)