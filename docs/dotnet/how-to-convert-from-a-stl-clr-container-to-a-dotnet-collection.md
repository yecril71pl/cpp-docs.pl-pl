---
title: 'Porady: konwertowanie kontenera STL/CLR na kolekcję .NET'
ms.date: 11/04/2016
helpviewer_keywords:
- STL/CLR Containers [STL/CLR]
- STL/CLR, converting to .NET collections
ms.assetid: 70b2dfd9-869c-4e0f-9a29-b1ee0cb0d107
ms.openlocfilehash: a4a754bbee08e93e2db9af50f98d7603fabcd8d4
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91498499"
---
# <a name="how-to-convert-from-a-stlclr-container-to-a-net-collection"></a>Porady: konwertowanie kontenera STL/CLR na kolekcję .NET

W tym temacie pokazano, jak konwertować kontenery STL/CLR na ich równoważne kolekcje platformy .NET. Na przykład pokazujemy, jak przekonwertować [wektor](../dotnet/vector-stl-clr.md) STL/CLR na platformę .NET <xref:System.Collections.Generic.ICollection%601> oraz jak skonwertować [mapę](../dotnet/map-stl-clr.md) STL/CLR na platformę .NET <xref:System.Collections.Generic.IDictionary%602> , ale procedura jest podobna dla wszystkich kolekcji i kontenerów.

### <a name="to-create-a-collection-from-a-container"></a>Aby utworzyć kolekcję z kontenera

1. Użyj jednej z następujących metod:

   - Aby skonwertować część kontenera, wywołaj funkcję [make_collection](./adapter-stl-clr.md#make_collection) i przekaż iterator BEGIN i End ITERATOR kontenera STL/CLR do skopiowania do kolekcji programu .NET. Ta funkcja szablonu przyjmuje Iteratory STL/CLR jako argument szablonu. Pierwszy przykład ilustruje tę metodę.

   - Aby przekonwertować cały kontener, należy rzutować go do odpowiedniego interfejsu kolekcji lub kolekcji interfejsów programu .NET. Drugi przykład ilustruje tę metodę.

## <a name="examples"></a>Przykłady

W tym przykładzie tworzymy kod STL/CLR `vector` i dodamy do niego 5 elementów. Następnie tworzymy kolekcję platformy .NET przez wywołanie `make_collection` funkcji. Na koniec zostanie wyświetlona zawartość nowo utworzonej kolekcji.

```cpp
// cliext_convert_vector_to_icollection.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/vector>

using namespace cliext;
using namespace System;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    cliext::vector<int> primeNumbersCont;
    primeNumbersCont.push_back(2);
    primeNumbersCont.push_back(3);
    primeNumbersCont.push_back(5);
    primeNumbersCont.push_back(7);
    primeNumbersCont.push_back(11);

    System::Collections::Generic::ICollection<int> ^iColl =
        make_collection<cliext::vector<int>::iterator>(
            primeNumbersCont.begin() + 1,
            primeNumbersCont.end() - 1);

    Console::WriteLine("The contents of the System::Collections::Generic::ICollection are:");
    for each (int i in iColl)
    {
        Console::WriteLine(i);
    }
}
```

```Output
The contents of the System::Collections::Generic::ICollection are:
3
5
7
```

W tym przykładzie tworzymy kod STL/CLR `map` i dodamy do niego 5 elementów. Następnie utworzymy platformę .NET <xref:System.Collections.Generic.IDictionary%602> i przypiszemy `map` ją bezpośrednio. Na koniec zostanie wyświetlona zawartość nowo utworzonej kolekcji.

```cpp
// cliext_convert_map_to_idictionary.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/map>

using namespace cliext;
using namespace System;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    cliext::map<float, int> ^aMap = gcnew cliext::map<float, int>;
    aMap->insert(cliext::make_pair<float, int>(42.0, 42));
    aMap->insert(cliext::make_pair<float, int>(13.0, 13));
    aMap->insert(cliext::make_pair<float, int>(74.0, 74));
    aMap->insert(cliext::make_pair<float, int>(22.0, 22));
    aMap->insert(cliext::make_pair<float, int>(0.0, 0));

    System::Collections::Generic::IDictionary<float, int> ^iDict = aMap;

    Console::WriteLine("The contents of the IDictionary are:");
    for each (KeyValuePair<float, int> ^kvp in iDict)
    {
        Console::WriteLine("Key: {0:F} Value: {1}", kvp->Key, kvp->Value);
    }
}
```

```Output
The contents of the IDictionary are:
Key: 0.00 Value: 0
Key: 13.00 Value: 13
Key: 22.00 Value: 22
Key: 42.00 Value: 42
Key: 74.00 Value: 74
```

## <a name="see-also"></a>Zobacz też

[Dokumentacja biblioteki STL/CLR](../dotnet/stl-clr-library-reference.md)<br/>
[Instrukcje: konwertowanie kolekcji .NET na kontener STL/CLR](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)<br/>
[range_adapter (STL/CLR)](./adapter-stl-clr.md#range_adapter)
