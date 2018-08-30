---
title: 'Porady: Definiowanie konstruktory przenoszące i przenoszące operatory przypisania (C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 03/05/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- move constructor [C++]
ms.assetid: e75efe0e-4b74-47a9-96ed-4e83cfc4378d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f414871477e8d263546833cb71496f5795dd4671
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43204990"
---
# <a name="move-constructors-and-move-assignment-operators-c"></a>Konstruktory przenoszące i przenoszące operatory przypisania (C++)
W tym temacie opisano sposób pisania *Konstruktor przenoszący* i operator przypisania przenoszenia dla klasy języka C++. Konstruktor przenoszący umożliwia zasoby należące do obiektem wartościowanym prawostronnie do przeniesienia do l-wartości bez kopiowania. Aby uzyskać więcej informacji dotyczących semantyki przenoszenia, zobacz [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
 Ten temat opiera się na następującej klasy C++ `MemoryBlock`, która zarządza buforem pamięci.  
  
```cpp  
// MemoryBlock.h  
#pragma once  
#include <iostream>  
#include <algorithm>  
  
class MemoryBlock  
{  
public:  
  
   // Simple constructor that initializes the resource.  
   explicit MemoryBlock(size_t length)  
      : _length(length)  
      , _data(new int[length])  
   {  
      std::cout << "In MemoryBlock(size_t). length = "  
                << _length << "." << std::endl;  
   }  
  
   // Destructor.  
   ~MemoryBlock()  
   {  
      std::cout << "In ~MemoryBlock(). length = "  
                << _length << ".";  
  
      if (_data != nullptr)  
      {  
         std::cout << " Deleting resource.";  
         // Delete the resource.  
         delete[] _data;  
      }  
  
      std::cout << std::endl;  
   }  
  
   // Copy constructor.  
   MemoryBlock(const MemoryBlock& other)  
      : _length(other._length)  
      , _data(new int[other._length])  
   {  
      std::cout << "In MemoryBlock(const MemoryBlock&). length = "   
                << other._length << ". Copying resource." << std::endl;  
  
      std::copy(other._data, other._data + _length, _data);  
   }  
  
   // Copy assignment operator.  
   MemoryBlock& operator=(const MemoryBlock& other)  
   {  
      std::cout << "In operator=(const MemoryBlock&). length = "   
                << other._length << ". Copying resource." << std::endl;  
  
      if (this != &other)  
      {  
         // Free the existing resource.  
         delete[] _data;  
  
         _length = other._length;  
         _data = new int[_length];  
         std::copy(other._data, other._data + _length, _data);  
      }  
      return *this;  
   }  
  
   // Retrieves the length of the data resource.  
   size_t Length() const  
   {  
      return _length;  
   }  
  
private:  
   size_t _length; // The length of the resource.  
   int* _data; // The resource.  
};  
```  
  
 W poniższych procedurach opisano jak napisać Konstruktor przenoszący i operator przypisania przenoszenia dla przykładowej klasy języka C++.  
  
### <a name="to-create-a-move-constructor-for-a-c-class"></a>Aby utworzyć Konstruktor przenoszący dla klasy języka C++  
  
1.  Zdefiniuj metodę pustego konstruktora, który przyjmuje odwołanie rvalue do typu klasy jako parametr, jak pokazano w poniższym przykładzie:  
  
    ```cpp  
    MemoryBlock(MemoryBlock&& other)  
       : _data(nullptr)  
       , _length(0)  
    {  
    }  
    ```  
  
2.  W Konstruktorze przenoszącym Przypisz elementy członkowskie danych klasy z obiektu źródłowego do obiektu, który jest konstruowany:  
  
    ```cpp  
    _data = other._data;  
    _length = other._length;  
    ```  
  
3.  Przypisz elementy członkowskie danych obiektu źródłowego do wartości domyślnych. Zapobiega to zwalnianiu zasobów (takich jak pamięć) wielokrotnie przez destruktor:  
  
    ```cpp  
    other._data = nullptr;  
    other._length = 0;  
    ```  
  
### <a name="to-create-a-move-assignment-operator-for-a-c-class"></a>Aby utworzyć operator przypisania przenoszenia dla klasy języka C++  

1.  Zdefiniuj pusty operator przypisania przyjmuje odwołanie rvalue do typu klasy jako parametr i zwraca odwołanie do typu klasy, jak pokazano w poniższym przykładzie:  
  
    ```cpp  
    MemoryBlock& operator=(MemoryBlock&& other)  
    {  
    }  
    ```  
  
2.  W operatorze przypisywania przenoszenia Dodaj instrukcję warunkową, która wykonuje żadnej operacji, jeśli użytkownik próbuje przypisać obiekt do samego siebie.  
  
    ```cpp  
    if (this != &other)  
    {  
    }  
    ```  
  
3.  W instrukcji warunkowej należy zwolnić wszystkie zasoby (takie jak pamięć) z obiektu, który jest przypisany do.  
  
     Poniższy przykład powoduje zwolnienie `_data` składowej z obiektu, który jest przypisany do:  
  
    ```cpp  
    // Free the existing resource.  
    delete[] _data;  
    ```  
  
     Wykonaj kroki 2 i 3 w pierwszej procedury, aby przenieść elementy członkowskie danych z obiektu źródłowego do obiektu, który jest konstruowany:  
  
    ```cpp  
    // Copy the data pointer and its length from the   
    // source object.  
    _data = other._data;  
    _length = other._length;  
  
    // Release the data pointer from the source object so that  
    // the destructor does not free the memory multiple times.  
    other._data = nullptr;  
    other._length = 0;  
    ```  
  
4.  Zwraca odwołanie do bieżącego obiektu, jak pokazano w poniższym przykładzie:  
  
    ```cpp  
    return *this;  
    ```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje kompletny Konstruktor przenoszący i operator przypisania przenoszenia dla `MemoryBlock` klasy:  
  
```cpp  
// Move constructor.  
MemoryBlock(MemoryBlock&& other)  
   : _data(nullptr)  
   , _length(0)  
{  
   std::cout << "In MemoryBlock(MemoryBlock&&). length = "   
             << other._length << ". Moving resource." << std::endl;  
  
   // Copy the data pointer and its length from the   
   // source object.  
   _data = other._data;  
   _length = other._length;  
  
   // Release the data pointer from the source object so that  
   // the destructor does not free the memory multiple times.  
   other._data = nullptr;  
   other._length = 0;  
}  
  
// Move assignment operator.  
MemoryBlock& operator=(MemoryBlock&& other)  
{  
   std::cout << "In operator=(MemoryBlock&&). length = "   
             << other._length << "." << std::endl;  
  
   if (this != &other)  
   {  
      // Free the existing resource.  
      delete[] _data;  
  
      // Copy the data pointer and its length from the   
      // source object.  
      _data = other._data;  
      _length = other._length;  
  
      // Release the data pointer from the source object so that  
      // the destructor does not free the memory multiple times.  
      other._data = nullptr;  
      other._length = 0;  
   }  
   return *this;  
}  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak semantyka przenoszenia może zwiększyć wydajność aplikacji. Przykład dodaje dwa elementy do obiektu wektora, a następnie wstawiono nowy element między dwa istniejące elementy. `vector` Klasa używa semantyki przenoszenia do wykonania operacji wstawiania efektywnie przez przeniesienie elementów wektora, nie zaś ich kopiowanie.  
  
```cpp  
// rvalue-references-move-semantics.cpp  
// compile with: /EHsc  
#include "MemoryBlock.h"  
#include <vector>  
  
using namespace std;  
  
int main()  
{  
   // Create a vector object and add a few elements to it.  
   vector<MemoryBlock> v;  
   v.push_back(MemoryBlock(25));  
   v.push_back(MemoryBlock(75));  
  
   // Insert a new element into the second position of the vector.  
   v.insert(v.begin() + 1, MemoryBlock(50));  
}  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```Output  
In MemoryBlock(size_t). length = 25.  
In MemoryBlock(MemoryBlock&&). length = 25. Moving resource.  
In ~MemoryBlock(). length = 0.  
In MemoryBlock(size_t). length = 75.  
In MemoryBlock(MemoryBlock&&). length = 25. Moving resource.  
In ~MemoryBlock(). length = 0.  
In MemoryBlock(MemoryBlock&&). length = 75. Moving resource.  
In ~MemoryBlock(). length = 0.  
In MemoryBlock(size_t). length = 50.  
In MemoryBlock(MemoryBlock&&). length = 50. Moving resource.  
In MemoryBlock(MemoryBlock&&). length = 50. Moving resource.  
In operator=(MemoryBlock&&). length = 75.  
In operator=(MemoryBlock&&). length = 50.  
In ~MemoryBlock(). length = 0.  
In ~MemoryBlock(). length = 0.  
In ~MemoryBlock(). length = 25. Deleting resource.  
In ~MemoryBlock(). length = 50. Deleting resource.  
In ~MemoryBlock(). length = 75. Deleting resource.  
```  
  
 Przed Visual Studio 2010 w tym przykładzie utworzone następujące dane wyjściowe:  
  
```Output  
In MemoryBlock(size_t). length = 25.  
In MemoryBlock(const MemoryBlock&). length = 25. Copying resource.  
In ~MemoryBlock(). length = 25. Deleting resource.  
In MemoryBlock(size_t). length = 75.  
In MemoryBlock(const MemoryBlock&). length = 25. Copying resource.  
In ~MemoryBlock(). length = 25. Deleting resource.  
In MemoryBlock(const MemoryBlock&). length = 75. Copying resource.  
In ~MemoryBlock(). length = 75. Deleting resource.  
In MemoryBlock(size_t). length = 50.  
In MemoryBlock(const MemoryBlock&). length = 50. Copying resource.  
In MemoryBlock(const MemoryBlock&). length = 50. Copying resource.  
In operator=(const MemoryBlock&). length = 75. Copying resource.  
In operator=(const MemoryBlock&). length = 50. Copying resource.  
In ~MemoryBlock(). length = 50. Deleting resource.  
In ~MemoryBlock(). length = 50. Deleting resource.  
In ~MemoryBlock(). length = 25. Deleting resource.  
In ~MemoryBlock(). length = 50. Deleting resource.  
In ~MemoryBlock(). length = 75. Deleting resource.  
```  
  
 Wersja tego przykładu, który używa semantyki przenoszenia jest bardziej wydajna niż wersja, która nie używa semantyki przenoszenia, ponieważ wykonuje mniejszą liczbę kopii, alokacji pamięci i operacji dezalokacji pamięci.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Aby zapobiec przeciekom zasobów, należy zawsze bezpłatne zasoby (takie jak pamięć, dojścia do plików i gniazda) w operatorze przypisania przenoszenia.  
  
 Aby zapobiec nieodwracalnemu niszczeniu zasobów, należy prawidłowo Obsługuj własny przydziału w operatorze przypisania przenoszenia.  
  
 Jeśli podasz zarówno konstruktora przenoszącego, jak i operator przypisania przenoszenia dla klasy, można wyeliminować nadmiarowy kod, pisząc Konstruktor przenoszący, aby wywołać operator przypisania przenoszenia. Poniższy przykład przedstawia poprawioną wersję konstruktora przenoszącego, który wywołuje operator przypisania przenoszenia:  
  
```cpp
// Move constructor.  
MemoryBlock(MemoryBlock&& other)  
   : _data(nullptr)  
   , _length(0)  
{  
   *this = std::move(other);  
}  
```  
  
 [Std::move](../standard-library/utility-functions.md#move) funkcji zachowuje własność rvalue *innych* parametru.  
  
## <a name="see-also"></a>Zobacz także  
 [Deklarator odwołania do wartości r: & &](../cpp/rvalue-reference-declarator-amp-amp.md)   
 [\<Narzędzia > Przenieś](https://msdn.microsoft.com/abef7e85-9dd6-4724-85da-d7f7fe95dca9)