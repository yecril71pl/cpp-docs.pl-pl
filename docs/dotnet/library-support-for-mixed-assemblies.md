---
title: "Obsługa bibliotek dla zestawów mieszanych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- msvcm90[d].dll
- mixed assemblies [C++], library support
- msvcmrt[d].lib
- libraries [C++], mixed assemblies
ms.assetid: 1229595c-9e9d-414d-b018-b4e4c727576d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6f999a75a8f818fccabada840a2a6e9fc70447cb
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="library-support-for-mixed-assemblies"></a>Obsługa bibliotek dla zestawów mieszanych
Visual C++ obsługuje korzystanie z biblioteki Standard C++, biblioteki plików wykonywalnych (CRT) ATL i MFC dla aplikacji skompilowanych z [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md). Dzięki temu istniejące aplikacje używające tych bibliotek do użycia jak również funkcje środowiska .NET Framework.  
  
 Ta obsługa wprowadza następujące nowe biblioteki DLL, a następnie zaimportuj:  
  
-   .Lib Msvcmrt [d] Jeśli skompiluj z/CLR. Zestawy mieszane łącza do tej biblioteki importu.  
  
 Ta obsługa zapewnia kilka korzyści związanych z nimi:  
  
-   CRT i standardowa biblioteka C++ są dostępne zarówno mieszanych i czysty kod. Nie są możliwe do zweryfikowania; CRT i podać standardowa biblioteka C++ ostatecznie wywołania nadal są kierowane do tego samego CRT i standardowa biblioteka C++, jak w przypadku korzystania z kodu macierzystego.  
  
-   Popraw ujednoliconą wyjątków w obrazach czysty i mieszanych.  
  
-   Inicjowanie statyczne zmiennych C++ w obrazach czysty i mieszanych.  
  
-   Obsługa zmiennych per-AppDomain i każdego procesu w kodzie zarządzanym.  
  
-   Rozwiązuje problemy blokady modułu ładującego, które dotyczą mieszanych bibliotek DLL skompilowany w Visual Studio 2003 i wcześniejszych wersjach.  
  
 Ponadto ta obsługa przedstawia następujące ograniczenia:  
  
-   Model CRT DLL jest obsługiwana dla kodu skompilowanego za pomocą/CLR.  
  
 Należy zaktualizować Twoje środowisko uruchomieniowe języka wspólnego (CLR) do wersji bieżącej, nie jest gwarantowana do pracy z wcześniejszymi wersjami. Kod skompilowanej za pomocą tych zmian nie będzie działać na wersji środowiska CLR 1.x.  
  
## <a name="see-also"></a>Zobacz też  
 [Zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md)