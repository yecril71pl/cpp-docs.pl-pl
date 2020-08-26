---
title: Odwołanie do biblioteki STL/CLR
ms.date: 09/18/2018
ms.topic: reference
helpviewer_keywords:
- STL/CLR Library
- STL/CLR, redistribution
- cliext directory
ms.assetid: a9d9ca00-7bf2-48c1-b205-3ae6f8c25f82
ms.openlocfilehash: e6804dab814eca4ecc5fd23c74cbbb21eac3be77
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839702"
---
# <a name="stlclr-library-reference"></a>Odwołanie do biblioteki STL/CLR

Biblioteka STL/CLR udostępnia interfejs podobny do kontenerów standardowej biblioteki języka C++ do użycia z C++ i .NET Framework środowiska uruchomieniowego języka wspólnego (CLR). Język STL/CLR jest całkowicie oddzielony od implementacji standardowej biblioteki języka C++ przez firmę Microsoft. Język STL/CLR jest obsługiwany w przypadku starszej obsługi, ale nie jest on aktualizowany przy użyciu standardu C++. Zdecydowanie zalecamy korzystanie z natywnych kontenerów [standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md) zamiast STL/CLR wszędzie tam, gdzie to możliwe.

Aby użyć STL/CLR:

- Uwzględnij nagłówki z **cliext** w podkatalogu zamiast zwykłych odpowiedników standardowej biblioteki języka C++.

- Kwalifikuj nazwy bibliotek `cliext::` zamiast `std::` .

Biblioteka STL/CLR udostępnia interfejs przypominający STL do użycia z językiem C++ i .NET Framework środowiska uruchomieniowego języka wspólnego (CLR). Ta biblioteka jest utrzymywana dla starszej obsługi, ale nie jest aktualizowana przy użyciu standardu C++. Zdecydowanie zalecamy użycie natywnych kontenerów [standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md) zamiast STL/CLR.

## <a name="in-this-section"></a>W tej sekcji

[cliext przestrzeń nazw](../dotnet/cliext-namespace.md)<br/>
Omawia przestrzeń nazw, która zawiera wszystkie typy biblioteki STL/CLR.

[Kontenery STL/CLR](../dotnet/stl-clr-containers.md)<br/>
Zawiera omówienie kontenerów, które znajdują się w standardowej bibliotece języka C++, w tym wymagania dotyczące elementów kontenera, typów elementów, które mogą być wstawiane, i problemów z własnością.

[Wymagania dotyczące elementów kontenera STL/CLR](../dotnet/requirements-for-stl-clr-container-elements.md)<br/>
Opisuje minimalne wymagania dla wszystkich typów referencyjnych, które są wstawiane do kontenerów standardowej biblioteki języka C++.

[Instrukcje: konwertowanie kolekcji .NET na kontener STL/CLR](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)<br/>
Opisuje sposób konwersji kolekcji .NET na kontener STL/CLR.

[Instrukcje: konwertowanie kontenera STL/CLR na kolekcję .NET](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)<br/>
Opisuje sposób konwersji kontenera STL/CLR na kolekcję .NET.

[Instrukcje: Uwidacznianie kontenera STL/CLR z zestawu](../dotnet/how-to-expose-an-stl-clr-container-from-an-assembly.md)<br/>
Pokazuje, jak wyświetlić elementy kilku kontenerów STL/CLR, które są zapisywane w zestawie języka C++.

Ponadto w tej sekcji opisano również następujące składniki biblioteki STL/CLR:

:::row:::
   :::column span="":::
      [`adapter` (STL/CLR)](../dotnet/adapter-stl-clr.md)\
      [`algorithm` (STL/CLR)](../dotnet/algorithm-stl-clr.md)\
      [`deque` (STL/CLR)](../dotnet/deque-stl-clr.md)\
      [`for each`, `in`](../dotnet/for-each-in.md)\
      [`functional` (STL/CLR)](../dotnet/functional-stl-clr.md)\
      [`hash_map` (STL/CLR)](../dotnet/hash-map-stl-clr.md)\
      [`hash_multimap` (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)\
      [`hash_multiset` (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)\
      [`hash_set` (STL/CLR)](../dotnet/hash-set-stl-clr.md)\
      [`list` (STL/CLR)](../dotnet/list-stl-clr.md)\
   :::column-end:::
   :::column span="":::
      [`map` (STL/CLR)](../dotnet/map-stl-clr.md)\
      [`multimap` (STL/CLR)](../dotnet/multimap-stl-clr.md)\
      [`multiset` (STL/CLR)](../dotnet/multiset-stl-clr.md)\
      [`numeric` (STL/CLR)](../dotnet/numeric-stl-clr.md)\
      [`priority_queue` (STL/CLR)](../dotnet/priority-queue-stl-clr.md)\
      [`queue` (STL/CLR)](../dotnet/queue-stl-clr.md)\
      [`set` (STL/CLR)](../dotnet/set-stl-clr.md)\
      [`stack` (STL/CLR)](../dotnet/stack-stl-clr.md)\
      [`utility` (STL/CLR)](../dotnet/utility-stl-clr.md)\
      [`vector` (STL/CLR)](../dotnet/vector-stl-clr.md)\
   :::column-end:::
:::row-end:::

## <a name="see-also"></a>Zobacz też

[Standardowa biblioteka języka C++](../standard-library/cpp-standard-library-reference.md)
