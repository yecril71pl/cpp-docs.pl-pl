---
title: "Obsługa bibliotek dla zestawów mieszanych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- msvcm90[d].dll
- mixed assemblies [C++], library support
- msvcmrt[d].lib
- libraries [C++], mixed assemblies
ms.assetid: 1229595c-9e9d-414d-b018-b4e4c727576d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 497900112bedc9c16b88078ab2b682b0357eb9bd
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="library-support-for-mixed-assemblies"></a>Obsługa bibliotek dla zestawów mieszanych
Visual C++ obsługuje korzystanie z biblioteki Standard C++, biblioteki plików wykonywalnych (CRT) ATL i MFC dla aplikacji skompilowanych z [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md). Dzięki temu istniejące aplikacje używające tych bibliotek do użycia jak również funkcje środowiska .NET Framework.  
  
 Ta obsługa wprowadza następujące nowe biblioteki DLL, a następnie zaimportuj:  
  
-   .Lib Msvcmrt [d] Jeśli skompiluj z/CLR. Zestawy mieszane łącza do tej biblioteki importu.  
  
-   Msvcm90 dll [d] i [d] Msvcurt .lib, jeśli skompiluj z/CLR: pure. Biblioteka DLL jest zestawem mieszanych zapewnianie zarządzanej obsługi czas uruchomienia C (CRT) i jest częścią zestawu zarządzanego zainstalowany w globalnej pamięci podręcznej zestawów (GAC). Zestawy czyste łącze do tej biblioteki importowanej oraz zakończenia zapasowej powiązany z Msvcm90.dll.  
  
 Ta obsługa zapewnia kilka korzyści związanych z nimi:  
  
-   CRT i standardowa biblioteka C++ są dostępne zarówno mieszanych i czysty kod. Nie są możliwe do zweryfikowania; CRT i podać standardowa biblioteka C++ ostatecznie wywołania nadal są kierowane do tego samego CRT i standardowa biblioteka C++, jak w przypadku korzystania z kodu macierzystego.  
  
-   Popraw ujednoliconą wyjątków w obrazach czysty i mieszanych.  
  
-   Inicjowanie statyczne zmiennych C++ w obrazach czysty i mieszanych.  
  
-   Obsługa zmiennych per-AppDomain i każdego procesu w kodzie zarządzanym.  
  
-   Rozwiązuje problemy blokady modułu ładującego, które dotyczą mieszanych bibliotek DLL skompilowany w Visual Studio 2003 i wcześniejszych wersjach.  
  
 Ponadto ta obsługa przedstawia następujące ograniczenia:  
  
-   Jest obsługiwana tylko modelu CRT DLL (zarówno dla kodu skompilowanego z opcją/CLR lub/CLR: pure).  
  
-   Nie można mieszać czysty i mieszanych obiektów w jednym obrazie, użycie tych obiektów bibliotek języka Visual C++ (ponieważ wszystkie obiekty muszą być czystym czystego obrazu). Jeśli to zrobisz, pojawi się błędy w czasie konsolidacji.  
  
 Należy zaktualizować Twoje środowisko uruchomieniowe języka wspólnego (CLR) do wersji bieżącej, nie jest gwarantowana do pracy z wcześniejszymi wersjami. Kod skompilowanej za pomocą tych zmian nie będzie działać na wersji środowiska CLR 1.x.  
  
## <a name="see-also"></a>Zobacz też  
 [Zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md)