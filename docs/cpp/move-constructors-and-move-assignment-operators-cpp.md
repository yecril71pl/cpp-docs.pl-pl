---
title: 'Porady: Definiowanie konstruktory przenoszenia i przenoszące operatory przypisania (C++) | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: ad5f54bc0366b0da9286631294a10f4904b7cb30
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="move-constructors-and-move-assignment-operators-c"></a>Konstruktory przenoszące i przenoszące operatory przypisania (C++)
W tym temacie opisano sposób zapisania *przenoszenie konstruktora* i operator przypisania przenoszenia, dla klasy C++. Konstruktor przenoszący umożliwia zasobów należących do r-wartości obiektu do przeniesienia do l-wartością bez kopiowania. Aby uzyskać więcej informacji na temat semantyki przenoszenia zobacz [deklarator odwołania do r-wartości: & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
 W tym temacie opisano następujące klasy C++, `MemoryBlock`, która zarządza bufora pamięci.  
  
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
  
 Poniższe procedury opisano sposób zapisu Konstruktor przenoszący oraz operator przypisania przenoszenia, na przykład klasy C++.  
  
### <a name="to-create-a-move-constructor-for-a-c-class"></a>Aby utworzyć Konstruktor przenoszący dla klasy C++  
  
1.  Zdefiniuj metodę pustego konstruktora, która przyjmuje jako jego parametr odwołania do r-wartości na typ klasy, jak pokazano w poniższym przykładzie:  
  
    ```cpp  
    MemoryBlock(MemoryBlock&& other)  
       : _data(nullptr)  
       , _length(0)  
    {  
    }  
    ```  
  
2.  W Konstruktorze przenoszenia Przypisz elementy członkowskie danych klasy z obiektu źródłowego do obiektu, który jest budowany:  
  
    ```cpp  
    _data = other._data;  
    _length = other._length;  
    ```  
  
3.  Elementy członkowskie danych obiektu źródłowego można przypisać wartości domyślne. Zapobiega to zwolnić zasobów (np. pamięci) wielokrotnie destruktor:  
  
    ```cpp  
    other._data = nullptr;  
    other._length = 0;  
    ```  
  
### <a name="to-create-a-move-assignment-operator-for-a-c-class"></a>Aby utworzyć operator przypisania przenoszenia, dla klasy C++  

1.  Definiowanie operatora przypisania pusta, która przyjmuje odwołania do r-wartości na typ klasy, jak jej parametr i zwraca odwołanie do typu klasy, jak pokazano w poniższym przykładzie:  
  
    ```cpp  
    MemoryBlock& operator=(MemoryBlock&& other)  
    {  
    }  
    ```  
  
2.  W operator przypisania przenoszenia Dodaj instrukcji warunkowej, Jeśli spróbujesz przypisać obiekt do siebie nie wykonuje żadnej operacji.  
  
    ```cpp  
    if (this != &other)  
    {  
    }  
    ```  
  
3.  W instrukcji warunkowej bez żadnych zasobów (np. pamięci) z obiektu, który jest przypisany do.  
  
     Poniższy przykład powoduje zwolnienie `_data` elementu członkowskiego z obiektu, który jest przypisany do:  
  
    ```cpp  
    // Free the existing resource.  
    delete[] _data;  
    ```  
  
     Wykonaj kroki 2 i 3 w ramach pierwszej procedury można przetransferować elementy członkowskie danych z obiektu źródłowego na obiekt, który jest budowany:  
  
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
 W poniższym przykładzie przedstawiono pełną przenoszenie konstruktora oraz przenoszący operator przypisania dla `MemoryBlock` klasy:  
  
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
 W poniższym przykładzie pokazano, jak semantyki przenoszenia może poprawić wydajność aplikacji. Przykład dodaje dwa elementy do obiektu vector i wstawia nowy element między dwoma elementami istniejących. `vector` Używa klasy Przenieś semantyki można wykonać operacji wstawiania efektywnie przenosząc elementów wektora zamiast kopiować je.  
  
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
  
```  
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
  
```  
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
  
 Wersja tego przykładu, że używa przenosić semantyki jest bardziej efektywne niż wersja, które nie korzystają bezpośrednio z semantyki przenoszenia, ponieważ wykonuje mniej kopiowania, Alokacja pamięci i operacji cofania alokacji pamięci.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Aby zapobiec przecieków zasobów, zawsze wolne w operator przypisania przenoszenia zasobów (np. pamięci, dojścia do plików i gniazda).  
  
 Aby zapobiec nieodwracalny zniszczenie zasobów, poprawnie obsługiwać własny przypisanie operator przypisania przenoszenia.  
  
 Jeśli podasz zarówno Konstruktor przenoszenia i operator przypisania przenoszenia dla klasy można wyeliminować nadmiarowy kod pisząc Konstruktor przenoszący operator przypisania przenoszenia wywołać. W poniższym przykładzie przedstawiono nowej wersji Konstruktor przenoszenia, która wywołuje operator przypisania przenoszenia:  
  
```  
// Move constructor.  
MemoryBlock(MemoryBlock&& other)  
   : _data(nullptr)  
   , _length(0)  
{  
   *this = std::move(other);  
}  
```  
  
 [Std::move](../standard-library/utility-functions.md#move) funkcja zachowuje r-wartości właściwości `other` parametru.  
  
## <a name="see-also"></a>Zobacz też  
 [Deklarator odwołania do wartości r: & &](../cpp/rvalue-reference-declarator-amp-amp.md)   
 [\<narzędzie > Przenieś](http://msdn.microsoft.com/en-us/abef7e85-9dd6-4724-85da-d7f7fe95dca9)