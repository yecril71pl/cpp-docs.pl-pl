---
title: Odwołanie do biblioteki STL/CLR
ms.date: 09/18/2018
ms.topic: reference
helpviewer_keywords:
- STL/CLR Library
- STL/CLR, redistribution
- cliext directory
ms.assetid: a9d9ca00-7bf2-48c1-b205-3ae6f8c25f82
ms.openlocfilehash: d5a2f3f9ceb62cf127d63c15131bf99646ebae4a
ms.sourcegitcommit: fbc05d8581913bca6eff664e5ecfcda8e471b8b1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/25/2019
ms.locfileid: "56809623"
---
# <a name="stlclr-library-reference"></a>Odwołanie do biblioteki STL/CLR

Biblioteki STL/CLR udostępnia interfejs, podobnie jak kontenery standardowej biblioteki języka C++ do użytku z C++ i .NET Framework środowisko uruchomieniowe języka wspólnego (CLR). STL/CLR jest całkowicie niezależna od implementacji Microsoft standardowej biblioteki języka C++. STL/CLR jest zachowywana na potrzeby obsługi starszej wersji, ale nie był cały czas aktualny ze standardem C++. Zdecydowanie zalecamy używanie natywnych [standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md) kontenery zamiast STL/CLR, jeśli to możliwe.

Aby użyć STL/CLR:

- Zawierają nagłówki z **cliext —** dołączanego podkatalogu zamiast zwykle odpowiedników standardowej biblioteki języka C++.

- Kwalifikacja nazw biblioteki z `cliext::` zamiast `std::`.

Biblioteki STL/CLR interfejs STL podobne do użytku z C++ i .NET Framework środowisko uruchomieniowe języka wspólnego (CLR). Ta biblioteka jest zachowywana na potrzeby obsługi starszej wersji, ale nie był cały czas aktualny ze standardem C++. Zdecydowanie zalecamy używanie natywnych [standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md) kontenery zamiast STL/CLR.

## <a name="in-this-section"></a>W tej sekcji

[Przestrzeń nazw cliext](../dotnet/cliext-namespace.md)<br/>
W tym artykule omówiono przestrzeni nazw, który zawiera wszystkie rodzaje biblioteki STL/CLR.

[Kontenery STL/CLR](../dotnet/stl-clr-containers.md)<br/>
Zawiera omówienie kontenerów, które znajdują się w standardowej biblioteki C++, włącznie z wymaganiami dotyczącymi elementów kontenera, typów elementów, które mogą być wstawiane i kwestie własnościowe.

[Wymagania dotyczące elementów kontenera STL/CLR](../dotnet/requirements-for-stl-clr-container-elements.md)<br/>
Opisuje minimalne wymagania dla wszystkich typów odniesienia, które są wstawiane do kontenerów standardowej biblioteki języka C++.

[Instrukcje: konwertowanie kolekcji .NET na kontener STL/CLR](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)<br/>
W tym artykule opisano sposób konwertowania kolekcji .NET na kontener STL/CLR.

[Instrukcje: konwertowanie kontenera STL/CLR na kolekcję .NET](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)<br/>
W tym artykule opisano sposób konwertowania kontenera STL/CLR na kolekcję .NET.

[Instrukcje: uwidacznianie kontenera STL/CLR z zestawu](../dotnet/how-to-expose-an-stl-clr-container-from-an-assembly.md)<br/>
W tym temacie przedstawiono sposób wyświetlać elementy kilku kontenerów STL/CLR napisane w zestawie C++.

Ponadto w tej sekcji opisano również następujące składniki STL/CLR:

|||
|-|-|
|[adapter (STL/CLR)](../dotnet/adapter-stl-clr.md)|[algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)|
|[deque (STL/CLR)](../dotnet/deque-stl-clr.md)|[for each, in](../dotnet/for-each-in.md)|
|[functional (STL/CLR)](../dotnet/functional-stl-clr.md)|[hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)|
|[hash_multimap (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)|[hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)|
|[hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)|[list (STL/CLR)](../dotnet/list-stl-clr.md)|
|[map (STL/CLR)](../dotnet/map-stl-clr.md)|[multimap (STL/CLR)](../dotnet/multimap-stl-clr.md)|
|[multiset (STL/CLR)](../dotnet/multiset-stl-clr.md)|[numeric (STL/CLR)](../dotnet/numeric-stl-clr.md)|
|[priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)|[queue (STL/CLR)](../dotnet/queue-stl-clr.md)|
|[set (STL/CLR)](../dotnet/set-stl-clr.md)|[stack (STL/CLR)](../dotnet/stack-stl-clr.md)|
|[utility (STL/CLR)](../dotnet/utility-stl-clr.md)|[vector (STL/CLR)](../dotnet/vector-stl-clr.md)|

## <a name="see-also"></a>Zobacz też

[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)
