---
title: 'Porady: konwertowanie kolekcji .NET na kontener STL/CLR'
ms.date: 11/04/2016
helpviewer_keywords:
- STL/CLR, converting from .NET collections
- STL/CLR Containers [STL/CLR]
ms.assetid: bb927c48-78e8-4150-bd0b-787c651f4a87
ms.openlocfilehash: 39c2beda6ae95783a2a29134013d6f01288a29b6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431151"
---
# <a name="how-to-convert-from-a-net-collection-to-a-stlclr-container"></a>Porady: konwertowanie kolekcji .NET na kontener STL/CLR

W tym temacie przedstawiono sposób konwertowania kolekcji .NET do ich równoważne kontenery STL/CLR. Jako przykład przedstawiono, jak przekonwertować .NET <xref:System.Collections.Generic.List%601> do STL/CLR [wektor](../dotnet/vector-stl-clr.md) oraz sposobach przekształcania .NET <xref:System.Collections.Generic.Dictionary%602> do STL/CLR [mapy](../dotnet/map-stl-clr.md), ale procedura jest podobna do wszystkich kolekcji i kontenery .

### <a name="to-create-a-container-from-a-collection"></a>Aby utworzyć kontener z kolekcji

1. Aby przekonwertować całą kolekcję, Tworzenie kontenera STL/CLR i przekazać kolekcji do konstruktora.

   W pierwszym przykładzie pokazano tej procedury.

-LUB-

1. Tworzenie ogólnych kontenera STL/CLR, tworząc [collection_adapter —](../dotnet/collection-adapter-stl-clr.md) obiektu. Tej klasy szablonu przyjmuje kolekcji interfejs platformy .NET jako argument. Aby sprawdzić, interfejsy, które są obsługiwane, zobacz [collection_adapter — (STL/CLR)](../dotnet/collection-adapter-stl-clr.md).

1. Skopiuj zawartość kolekcji .NET do kontenera. Można to zrobić przy użyciu STL/CLR [algorytm](../dotnet/algorithm-stl-clr.md), lub przez Iterowanie przez kolekcję .NET i wstawianie kopię każdy element do kontenera STL/CLR.

   W drugim przykładzie pokazano tej procedury.

## <a name="example"></a>Przykład

W tym przykładzie tworzymy ogólnego <xref:System.Collections.Generic.List%601> i dodać elementy 5 do niego. Następnie tworzymy `vector` przy użyciu konstruktora, który przyjmuje <xref:System.Collections.Generic.IEnumerable%601> jako argument.

```
// cliext_convert_list_to_vector.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/algorithm>
#include <cliext/vector>

using namespace System;
using namespace System::Collections;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    List<int> ^primeNumbersColl = gcnew List<int>();
    primeNumbersColl->Add(2);
    primeNumbersColl->Add(3);
    primeNumbersColl->Add(5);
    primeNumbersColl->Add(7);
    primeNumbersColl->Add(11);

    cliext::vector<int> ^primeNumbersCont =
        gcnew cliext::vector<int>(primeNumbersColl);

    Console::WriteLine("The contents of the cliext::vector are:");
    cliext::vector<int>::const_iterator it;
    for (it = primeNumbersCont->begin(); it != primeNumbersCont->end(); it++)
    {
        Console::WriteLine(*it);
    }
}
```

```Output
The contents of the cliext::vector are:
2
3
5
7
11
```

## <a name="example"></a>Przykład

W tym przykładzie tworzymy ogólnego <xref:System.Collections.Generic.Dictionary%602> i dodać elementy 5 do niego. Następnie tworzymy `collection_adapter` opakowywać <xref:System.Collections.Generic.Dictionary%602> jako prosty kontener STL/CLR. Na koniec utworzymy `map` i skopiuj zawartość <xref:System.Collections.Generic.Dictionary%602> do `map` przez Iterowanie `collection_adapter`. W trakcie tego procesu, możemy utworzyć nowej pary za pomocą `make_pair` funkcji i Wstaw nową parę bezpośrednio do `map`.

```
// cliext_convert_dictionary_to_map.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/algorithm>
#include <cliext/map>

using namespace System;
using namespace System::Collections;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    System::Collections::Generic::Dictionary<float, int> ^dict =
        gcnew System::Collections::Generic::Dictionary<float, int>();
    dict->Add(42.0, 42);
    dict->Add(13.0, 13);
    dict->Add(74.0, 74);
    dict->Add(22.0, 22);
    dict->Add(0.0, 0);

    cliext::collection_adapter<System::Collections::Generic::IDictionary<float, int>> dictAdapter(dict);
    cliext::map<float, int> aMap;
    for each (KeyValuePair<float, int> ^kvp in dictAdapter)
    {
        cliext::pair<float, int> aPair = cliext::make_pair(kvp->Key, kvp->Value);
        aMap.insert(aPair);
    }

    Console::WriteLine("The contents of the cliext::map are:");
    cliext::map<float, int>::const_iterator it;
    for (it = aMap.begin(); it != aMap.end(); it++)
    {
        Console::WriteLine("Key: {0:F} Value: {1}", it->first, it->second);
    }
}
```

```Output
The contents of the cliext::map are:
Key: 0.00 Value: 0
Key: 13.00 Value: 13
Key: 22.00 Value: 22
Key: 42.00 Value: 42
Key: 74.00 Value: 74
```

## <a name="see-also"></a>Zobacz też

[Dokumentacja biblioteki STL/CLR](../dotnet/stl-clr-library-reference.md)<br/>
[adapter (STL/CLR)](../dotnet/adapter-stl-clr.md)<br/>
[Instrukcje: konwertowanie kontenera STL/CLR na kolekcję .NET](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)