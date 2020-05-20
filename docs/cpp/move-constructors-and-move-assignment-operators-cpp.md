---
title: 'Instrukcje: Definiowanie konstruktorów przenoszenia i operatorów przypisania przenoszenia (C++)'
ms.date: 03/05/2018
helpviewer_keywords:
- move constructor [C++]
ms.assetid: e75efe0e-4b74-47a9-96ed-4e83cfc4378d
ms.openlocfilehash: 2c8fed15787ec4b347694d8c4e40bf7912f3421d
ms.sourcegitcommit: d4da3693f83a24f840e320e35c24a4a07cae68e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/18/2020
ms.locfileid: "83550774"
---
# <a name="move-constructors-and-move-assignment-operators-c"></a>Konstruktory przenoszące i przenoszące operatory przypisania (C++)

W tym temacie opisano, jak napisać *Konstruktor przenoszący* i operator przypisania przenoszenia dla klasy języka C++. Konstruktor przenoszący umożliwia przenoszenie zasobów należących do obiektu rvalue do lvalue bez kopiowania. Aby uzyskać więcej informacji na temat semantyki przenoszenia, zobacz [rvalue Reference deklarator:  &&](../cpp/rvalue-reference-declarator-amp-amp.md).

Ten temat jest oparty na następującej klasie C++, `MemoryBlock` która zarządza buforem pamięci.

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

W poniższych procedurach opisano, jak napisać Konstruktor przenoszący i operator przypisania przenoszenia dla przykładowej klasy C++.

### <a name="to-create-a-move-constructor-for-a-c-class"></a>Aby utworzyć Konstruktor przenoszenia dla klasy języka C++

1. Zdefiniuj pustą metodę konstruktora, która przyjmuje odwołanie rvalue do typu klasy jako parametr, jak pokazano w poniższym przykładzie:

    ```cpp
    MemoryBlock(MemoryBlock&& other)
       : _data(nullptr)
       , _length(0)
    {
    }
    ```

1. W konstruktorze przenoszenia Przypisz składowe danych klasy z obiektu źródłowego do obiektu, który jest konstruowany:

    ```cpp
    _data = other._data;
    _length = other._length;
    ```

1. Przypisz elementy członkowskie danych obiektu źródłowego do wartości domyślnych. Zapobiega to wykorzystaniu przez destruktora zasobów (takich jak pamięć) wiele razy:

    ```cpp
    other._data = nullptr;
    other._length = 0;
    ```

### <a name="to-create-a-move-assignment-operator-for-a-c-class"></a>Aby utworzyć operator przypisania przenoszenia dla klasy języka C++

1. Zdefiniuj pusty operator przypisania, który przyjmuje odwołanie rvalue do typu klasy jako parametr i zwraca odwołanie do typu klasy, jak pokazano w następującym przykładzie:

    ```cpp
    MemoryBlock& operator=(MemoryBlock&& other)
    {
    }
    ```

1. W operatorze przypisania przenoszenia Dodaj instrukcję warunkową, która nie wykonuje żadnej operacji, jeśli próbujesz przypisać obiekt do samego siebie.

    ```cpp
    if (this != &other)
    {
    }
    ```

1. W instrukcji warunkowej Zwolnij wszystkie zasoby (takie jak pamięć) z obiektu, do którego jest przypisany.

   Poniższy przykład zwalnia `_data` element członkowski z obiektu, który jest przypisywany do:

    ```cpp
    // Free the existing resource.
    delete[] _data;
    ```

   Wykonaj kroki 2 i 3 w pierwszej procedurze, aby przenieść elementy członkowskie danych z obiektu źródłowego do obiektu, który jest konstruowany:

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

1. Zwróć odwołanie do bieżącego obiektu, jak pokazano w następującym przykładzie:

    ```cpp
    return *this;
    ```

## <a name="example"></a>Przykład

Poniższy przykład pokazuje kompletny Konstruktor przenoszenia i operator przypisania przenoszenia dla `MemoryBlock` klasy:

```cpp
// Move constructor.
MemoryBlock(MemoryBlock&& other) noexcept
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
MemoryBlock& operator=(MemoryBlock&& other) noexcept
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

Poniższy przykład pokazuje, jak Semantyka przenoszenia może zwiększyć wydajność aplikacji. Przykład dodaje dwa elementy do obiektu Vector, a następnie wstawia nowy element między dwoma istniejącymi elementami. `vector`Klasa używa semantyki przenoszenia do wydajnego wykonywania operacji wstawiania przez przeniesienie elementów wektora zamiast ich kopiowania.

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
In MemoryBlock(MemoryBlock&&). length = 75. Moving resource.
In MemoryBlock(MemoryBlock&&). length = 25. Moving resource.
In ~MemoryBlock(). length = 0.
In ~MemoryBlock(). length = 0.
In MemoryBlock(size_t). length = 50.
In MemoryBlock(MemoryBlock&&). length = 50. Moving resource.
In MemoryBlock(MemoryBlock&&). length = 25. Moving resource.
In MemoryBlock(MemoryBlock&&). length = 75. Moving resource.
In ~MemoryBlock(). length = 0.
In ~MemoryBlock(). length = 0.
In ~MemoryBlock(). length = 0.
In ~MemoryBlock(). length = 25. Deleting resource.
In ~MemoryBlock(). length = 50. Deleting resource.
In ~MemoryBlock(). length = 75. Deleting resource.
```

Przed Visual Studio 2010 ten przykład wygenerował następujące dane wyjściowe:

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

Wersja tego przykładu, która używa semantyki przenoszenia, jest bardziej wydajna niż wersja, która nie korzysta z semantyki przenoszenia, ponieważ wykonuje mniej operacji kopiowania, alokacji pamięci i cofania alokacji pamięci.

## <a name="robust-programming"></a>Niezawodne programowanie

Aby zapobiec przeciekom zasobów, zawsze używaj bezpłatnych zasobów (takich jak pamięć, dojścia do plików i gniazda) w operatorze przypisania przenoszenia.

Aby zapobiec nieodwracalnemu zniszczeniu zasobów, należy prawidłowo obsłużyć własne przypisanie w operatorze przypisania przenoszenia.

Jeśli podajesz zarówno Konstruktor przenoszący, jak i operator przypisania przenoszenia dla klasy, możesz wyeliminować nadmiarowy kod przez napisanie konstruktora przenoszenia w celu wywołania operatora przypisania przenoszenia. W poniższym przykładzie przedstawiono poprawioną wersję konstruktora przenoszenia, która wywołuje operator przypisania przenoszenia:

```cpp
// Move constructor.
MemoryBlock(MemoryBlock&& other) noexcept
   : _data(nullptr)
   , _length(0)
{
   *this = std::move(other);
}
```

Funkcja [std:: Move](../standard-library/utility-functions.md#move) konwertuje lvalue `other` na rvalue.

## <a name="see-also"></a>Zobacz także

[Deklarator odwołania do wartości R: &&](../cpp/rvalue-reference-declarator-amp-amp.md)<br/>
[std:: Move](../standard-library/utility-functions.md#move)
