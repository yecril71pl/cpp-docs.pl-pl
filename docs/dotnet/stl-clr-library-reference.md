---
title: Odwołanie do biblioteki STL/CLR | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- STL/CLR Library
- STL/CLR, redistribution
- cliext directory
ms.assetid: a9d9ca00-7bf2-48c1-b205-3ae6f8c25f82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 78dc5c57ca000dfa03dba640c46cec16aaca133f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429478"
---
# <a name="stlclr-library-reference"></a>Odwołanie do biblioteki STL/CLR

Biblioteka STL/CLR to opakowanie podzbiór standardowej biblioteki C++ do użytku z C++ i .NET Framework środowisko uruchomieniowe języka wspólnego (CLR). Z STL/CLR można użyć wszystkich kontenerów, iteratorów i algorytmów standardowej biblioteki w środowisku zarządzanym.

Aby użyć STL/CLR:

- Zawierają nagłówki z **cliext —** dołączanego podkatalogu zamiast zwykle odpowiedników standardowej biblioteki języka C++.

- Kwalifikacja nazw biblioteki z `cliext::` zamiast `std::`.

STL/CLR ujawnia typy ogólne i interfejsy, których używa w scenariuszach między zestawami w zestawie .NET **Microsoft.VisualC.STLCLR.dll**. DLL jest zawarty w .NET Framework 3.5. Jeśli ponownie dystrybuujesz aplikacji korzystającej z STL/CLR należy uwzględnić programu .NET Framework 3.5, jak również innych bibliotek Visual C++, które używa projekt w sekcji zależności projektu Instalatora.

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