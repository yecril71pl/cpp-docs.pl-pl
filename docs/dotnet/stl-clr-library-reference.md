---
title: "Odwołanie do biblioteki STL/CLR | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- STL/CLR Library
- STL/CLR, redistribution
- cliext directory
ms.assetid: a9d9ca00-7bf2-48c1-b205-3ae6f8c25f82
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: aecb7c509fc1b072086a8772c3430c43b67350be
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="stlclr-library-reference"></a>Odwołanie do biblioteki STL/CLR
Biblioteka STL/CLR jest opakowanie podzbiór standardowa biblioteka C++ do użycia z C++ i .NET Framework środowisko uruchomieniowe języka wspólnego (CLR). Z STL/CLR można użyć wszystkich kontenerów, Iteratory i algorytmy biblioteki standardowej w środowisku zarządzanym.  
  
 Aby użyć STL/CLR:  
  
-   Zawiera nagłówków z **cliext** obejmują podkatalogu zamiast standardowego odpowiedniki standardowa biblioteka C++.  
  
-   Uprawnione nazwy bibliotek z `cliext::` zamiast `std::`.  
  
 STL/CLR ujawnia typy ogólne i interfejsy, używane w scenariuszach między zestawami w zestawie .NET **Microsoft.VisualC.STLCLR.dll**. Ta biblioteka DLL jest dołączony do programu .NET Framework 3.5. Wykonać ponowną dystrybucję aplikacji, która używa STL/CLR, należy uwzględnić programu .NET Framework 3.5, a także innych bibliotek języka Visual C++, które używa projektu, w sekcji zależności projektu Instalatora.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przestrzeń nazw cliext](../dotnet/cliext-namespace.md)  
 W tym artykule omówiono przestrzeni nazw, która zawiera wszystkie typy biblioteki STL/CLR.  
  
 [Kontenery STL/CLR](../dotnet/stl-clr-containers.md)  
 Zawiera omówienie kontenerów, które znajdują się w standardowa biblioteka C++, w tym wymagania dotyczące elementów kontenera, typy elementów, które mogą być wstawiane i własność problemy.  
  
 [Wymagania dotyczące elementów kontenera STL/CLR](../dotnet/requirements-for-stl-clr-container-elements.md)  
 Opisuje minimalne wymagania dla wszystkich typów odwołania, które są wstawiane do kontenerów standardowa biblioteka C++.  
  
 [Instrukcje: konwertowanie kolekcji .NET na kontener STL/CLR](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)  
 Opisuje sposób konwertowanie kolekcji .NET na kontener STL/CLR.  
  
 [Instrukcje: konwertowanie kontenera STL/CLR na kolekcję .NET](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)  
 Opisuje sposób konwertowanie kontenera STL/CLR na kolekcję .NET.  
  
 [Instrukcje: uwidacznianie kontenera STL/CLR z zestawu](../dotnet/how-to-expose-an-stl-clr-container-from-an-assembly.md)  
 Przedstawia sposób wyświetlania elementów w zestawie C++ kilka kontenery STL/CLR.  
  
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