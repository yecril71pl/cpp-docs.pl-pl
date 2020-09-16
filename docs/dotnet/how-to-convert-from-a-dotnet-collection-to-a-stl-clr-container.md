---
title: 'Porady: konwertowanie kolekcji .NET na kontener STL/CLR'
ms.date: 11/04/2016
helpviewer_keywords:
- STL/CLR, converting from .NET collections
- STL/CLR Containers [STL/CLR]
ms.assetid: bb927c48-78e8-4150-bd0b-787c651f4a87
ms.openlocfilehash: a7b2ee94f02e663690287ecfa6bc8a7230830a95
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686460"
---
# <a name="how-to-convert-from-a-net-collection-to-a-stlclr-container"></a>Porady: konwertowanie kolekcji .NET na kontener STL/CLR

W tym temacie pokazano, jak skonwertować kolekcje .NET do ich odpowiedników kontenerów STL/CLR. Przykład pokazuje, jak przekonwertować platformę .NET <xref:System.Collections.Generic.List%601> na [wektor](../dotnet/vector-stl-clr.md) STL/CLR oraz jak skonwertować platformę .NET <xref:System.Collections.Generic.Dictionary%602> na [mapę](../dotnet/map-stl-clr.md)STL/CLR, ale procedura jest podobna dla wszystkich kolekcji i kontenerów.

### <a name="to-create-a-container-from-a-collection"></a>Aby utworzyć kontener z kolekcji

1. Aby przekonwertować całą kolekcję, Utwórz kontener STL/CLR i przekaż kolekcję do konstruktora.

   Pierwszy przykład ilustruje tę procedurę.

— Lub —

1. Utwórz ogólny kontener STL/CLR przez utworzenie obiektu [collection_adapter](../dotnet/collection-adapter-stl-clr.md) . Ta klasa szablonu przyjmuje jako argument interfejs kolekcji .NET. Aby sprawdzić, które interfejsy są obsługiwane, zobacz [collection_adapter (STL/CLR)](../dotnet/collection-adapter-stl-clr.md).

1. Skopiuj zawartość kolekcji .NET do kontenera. Można to zrobić za pomocą [algorytmu](../dotnet/algorithm-stl-clr.md)STL/CLR lub przez iterację kolekcji .NET i wstawianie kopii każdego elementu do kontenera STL/CLR.

   Drugi przykład ilustruje tę procedurę.

## <a name="examples"></a>Przykłady

W tym przykładzie utworzymy rodzajowy <xref:System.Collections.Generic.List%601> i dodamy do niego 5 elementów. Następnie tworzymy `vector` przy użyciu konstruktora, który przyjmuje <xref:System.Collections.Generic.IEnumerable%601> jako argument.

```cpp
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

W tym przykładzie utworzymy rodzajowy <xref:System.Collections.Generic.Dictionary%602> i dodamy do niego 5 elementów. Następnie tworzymy, `collection_adapter` aby otoczyć obiekt <xref:System.Collections.Generic.Dictionary%602> jako prosty kontener STL/CLR. Na koniec tworzymy `map` i skopiujemy zawartość <xref:System.Collections.Generic.Dictionary%602> do elementu `map` przez iterację `collection_adapter` . W trakcie tego procesu tworzymy nową parę przy użyciu `make_pair` funkcji i wstawiamy nową parę bezpośrednio do `map` .

```cpp
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

## <a name="see-also"></a>Zobacz także

[Dokumentacja biblioteki STL/CLR](../dotnet/stl-clr-library-reference.md)<br/>
[adapter (STL/CLR)](../dotnet/adapter-stl-clr.md)<br/>
[Instrukcje: konwertowanie kontenera STL/CLR na kolekcję .NET](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)
