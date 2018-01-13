---
title: Specjalizacja szablonu (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: partial specialization of class templates
ms.assetid: f3c67c0b-3875-434a-b8d8-bb47e99cf4f0
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 572ef5ca7199fab5b9ffda686425cdd53547a60a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="template-specialization-c"></a>Specjalizacja szablonu (C++)

Szablony klas może być częściowo specjalizowany i wynikowa klasy jest nadal szablonu. Częściowa specjalizacja umożliwia kod szablonu do częściowo dostosowania dla określonych typów w sytuacjach, takich jak:  
  
-   Szablon ma wiele typów i tylko niektóre z nich musi być specjalizowany. Wynik jest szablon sparametryzowana pozostałych typów.  
  
-   Szablon ma tylko jeden typ, ale specjalizacji jest wymagany dla wskaźnika, odwołanie, wskaźnik do elementu członkowskiego lub typów wskaźnika funkcji. Specjalizacja, sam jest nadal szablonu wskazywał lub odwołuje się do typu.  
  
## <a name="example"></a>Przykład  
  
```cpp
// partial_specialization_of_class_templates.cpp  
template <class T> struct PTS {  
   enum {  
      IsPointer = 0,  
      IsPointerToDataMember = 0  
   };  
};  
  
template <class T> struct PTS<T*> {  
   enum {  
      IsPointer = 1,  
      IsPointerToDataMember = 0  
   };  
};  
  
template <class T, class U> struct PTS<T U::*> {  
   enum {  
      IsPointer = 0,  
      IsPointerToDataMember = 1  
   };  
};  
  
struct S{};  
  
extern "C" int printf_s(const char*,...);  
  
int main() {  
   S s, *pS;  
   int S::*ptm;  
   printf_s("PTS<S>::IsPointer == %d PTS<S>::IsPointerToDataMember == %d\n",   
           PTS<S>::IsPointer, PTS<S>:: IsPointerToDataMember);  
   printf_s("PTS<S*>::IsPointer == %d PTS<S*>::IsPointerToDataMember ==%d\n"  
           , PTS<S*>::IsPointer, PTS<S*>:: IsPointerToDataMember);  
   printf_s("PTS<int S::*>::IsPointer == %d PTS"  
           "<int S::*>::IsPointerToDataMember == %d\n",   
           PTS<int S::*>::IsPointer, PTS<int S::*>::   
           IsPointerToDataMember);  
}  
```  
  
```Output  
PTS<S>::IsPointer == 0 PTS<S>::IsPointerToDataMember == 0  
PTS<S*>::IsPointer == 1 PTS<S*>::IsPointerToDataMember ==0  
PTS<int S::*>::IsPointer == 0 PTS<int S::*>::IsPointerToDataMember == 1  
```  
  
## <a name="example"></a>Przykład

 Jeśli masz pobierającej dowolnego typu klasy kolekcji szablonu **T**, można utworzyć częściowej specjalizacji pobierającej dowolnego typu wskaźnika **T***. Poniższy kod przedstawia szablonu klasy kolekcji `Bag` i częściowa specjalizacja dla typów wskaźnika, w których kolekcji wyłuskań typów wskaźnika przed skopiowaniem ich do tablicy. Następnie kolekcji przechowuje wartości, które są wskazywał. Z oryginalnym szablonie tylko wskaźniki się czy były przechowywane w kolekcji, pozostawiając dane są narażone na usuwanie lub zmiana. W tej wersji specjalne wskaźnika kolekcji kodu do sprawdzenia wartości null wskaźnika w `add` metoda jest dodawana.  
  
```cpp
// partial_specialization_of_class_templates2.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
// Original template collection class.  
template <class T> class Bag {  
   T* elem;  
   int size;  
   int max_size;  
  
public:  
   Bag() : elem(0), size(0), max_size(1) {}  
   void add(T t) {  
      T* tmp;  
      if (size + 1 >= max_size) {  
         max_size *= 2;  
         tmp = new T [max_size];  
         for (int i = 0; i < size; i++)  
            tmp[i] = elem[i];  
         tmp[size++] = t;  
         delete[] elem;  
         elem = tmp;  
      }  
      else  
         elem[size++] = t;  
   }  
  
   void print() {  
      for (int i = 0; i < size; i++)  
         cout << elem[i] << " ";  
      cout << endl;  
   }  
};  
  
// Template partial specialization for pointer types.  
// The collection has been modified to check for NULL   
// and store types pointed to.  
template <class T> class Bag<T*> {  
   T* elem;  
   int size;  
   int max_size;  
  
public:  
   Bag() : elem(0), size(0), max_size(1) {}  
   void add(T* t) {  
      T* tmp;  
      if (t == NULL) {   // Check for NULL  
         cout << "Null pointer!" << endl;  
         return;  
      }  
  
      if (size + 1 >= max_size) {  
         max_size *= 2;  
         tmp = new T [max_size];  
         for (int i = 0; i < size; i++)  
            tmp[i] = elem[i];  
         tmp[size++] = *t;  // Dereference  
         delete[] elem;  
         elem = tmp;  
      }  
      else  
         elem[size++] = *t; // Dereference  
   }  
  
   void print() {  
      for (int i = 0; i < size; i++)  
         cout << elem[i] << " ";  
      cout << endl;  
   }  
};  
  
int main() {  
   Bag<int> xi;  
   Bag<char> xc;  
   Bag<int*> xp; // Uses partial specialization for pointer types.  
  
   xi.add(10);  
   xi.add(9);  
   xi.add(8);  
   xi.print();  
  
   xc.add('a');  
   xc.add('b');  
   xc.add('c');  
   xc.print();  
  
   int i = 3, j = 87, *p = new int[2];  
   *p = 8;  
   *(p + 1) = 100;  
   xp.add(&i);  
   xp.add(&j);  
   xp.add(p);  
   xp.add(p + 1);  
   p = NULL;  
   xp.add(p);  
   xp.print();  
}  
```  
  
```Output  
10 9 8   
a b c   
Null pointer!  
3 87 8 100   
```  
  
## <a name="example"></a>Przykład

 W poniższym przykładzie zdefiniowano szablonu klasy, która przyjmuje pary żadnych dwa typy i następnie definiuje częściowa specjalizacja szablonów klas wyspecjalizowanych tak, aby jeden z typów `int`. Specjalizacja definiuje metodę dodatkowe sortowania, która implementuje sortowanie proste bąbelków oparte na liczbę całkowitą.  
  
```cpp
// partial_specialization_of_class_templates3.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
template <class Key, class Value> class Dictionary {  
   Key* keys;  
   Value* values;  
   int size;  
   int max_size;  
public:  
   Dictionary(int initial_size) :  size(0) {  
      max_size = 1;  
      while (initial_size >= max_size)  
         max_size *= 2;  
      keys = new Key[max_size];  
      values = new Value[max_size];  
   }  
   void add(Key key, Value value) {  
      Key* tmpKey;  
      Value* tmpVal;  
      if (size + 1 >= max_size) {  
         max_size *= 2;  
         tmpKey = new Key [max_size];  
         tmpVal = new Value [max_size];  
         for (int i = 0; i < size; i++) {  
            tmpKey[i] = keys[i];  
            tmpVal[i] = values[i];  
         }  
         tmpKey[size] = key;  
         tmpVal[size] = value;  
         delete[] keys;  
         delete[] values;  
         keys = tmpKey;  
         values = tmpVal;  
      }  
      else {  
         keys[size] = key;  
         values[size] = value;  
      }  
      size++;  
   }  
  
   void print() {  
      for (int i = 0; i < size; i++)  
         cout << "{" << keys[i] << ", " << values[i] << "}" << endl;  
   }  
};  
  
// Template partial specialization: Key is specified to be int.  
template <class Value> class Dictionary<int, Value> {  
   int* keys;  
   Value* values;  
   int size;  
   int max_size;  
public:  
   Dictionary(int initial_size) :  size(0) {  
      max_size = 1;  
      while (initial_size >= max_size)  
         max_size *= 2;  
      keys = new int[max_size];  
      values = new Value[max_size];  
   }  
   void add(int key, Value value) {  
      int* tmpKey;  
      Value* tmpVal;  
      if (size + 1 >= max_size) {  
         max_size *= 2;  
         tmpKey = new int [max_size];  
         tmpVal = new Value [max_size];  
         for (int i = 0; i < size; i++) {  
            tmpKey[i] = keys[i];  
            tmpVal[i] = values[i];  
         }  
         tmpKey[size] = key;  
         tmpVal[size] = value;  
         delete[] keys;  
         delete[] values;  
         keys = tmpKey;  
         values = tmpVal;  
      }  
      else {  
         keys[size] = key;  
         values[size] = value;  
      }  
      size++;  
   }  
  
   void sort() {  
      // Sort method is defined.  
      int smallest = 0;  
      for (int i = 0; i < size - 1; i++) {  
         for (int j = i; j < size; j++) {  
            if (keys[j] < keys[smallest])  
               smallest = j;  
         }  
         swap(keys[i], keys[smallest]);  
         swap(values[i], values[smallest]);  
      }  
   }  
  
   void print() {  
      for (int i = 0; i < size; i++)  
         cout << "{" << keys[i] << ", " << values[i] << "}" << endl;  
   }  
};  
  
int main() {  
   Dictionary<char*, char*>* dict = new Dictionary<char*, char*>(10);  
   dict->print();  
   dict->add("apple", "fruit");  
   dict->add("banana", "fruit");  
   dict->add("dog", "animal");  
   dict->print();  
  
   Dictionary<int, char*>* dict_specialized = new Dictionary<int, char*>(10);  
   dict_specialized->print();  
   dict_specialized->add(100, "apple");  
   dict_specialized->add(101, "banana");  
   dict_specialized->add(103, "dog");  
   dict_specialized->add(89, "cat");  
   dict_specialized->print();  
   dict_specialized->sort();  
   cout << endl << "Sorted list:" << endl;  
   dict_specialized->print();  
}  
```  
  
```Output  
{apple, fruit}  
{banana, fruit}  
{dog, animal}  
{100, apple}  
{101, banana}  
{103, dog}  
{89, cat}  
  
Sorted list:  
{89, cat}  
{100, apple}  
{101, banana}  
{103, dog}  
```  
