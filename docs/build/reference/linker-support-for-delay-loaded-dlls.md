---
title: "Obsługa konsolidatora dla bibliotek DLL załadowanych z opóźnieniem | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: delayed loading of DLLs, linker support
ms.assetid: b2d7e449-2809-42b1-9c90-2c0ca5e31a14
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 83e75df963889730e4514c38d0551af241a788fa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-support-for-delay-loaded-dlls"></a>Obsługa konsolidatora dla bibliotek DLL załadowanych z opóźnieniem
Konsolidatora Visual C++ obsługuje teraz opóźnione ładowanie bibliotek DLL. To zwalnia od konieczność użycia funkcji zestawu SDK systemu Windows **LoadLibrary** i **GetProcAddress** do zaimplementowania opóźnienie załadowanie DLL.  
  
 Przed Visual C++ 6.0, jedynym sposobem, aby załadować biblioteki DLL w czasie wykonywania była za pomocą **LoadLibrary** i **GetProcAddress**; systemu operacyjnego czy ładowanie biblioteki DLL gdy plik wykonywalny lub biblioteka DLL przy użyciu została załadowana.  
  
 Visual C++ 6.0, począwszy od podczas łączenia statycznie z biblioteki DLL, konsolidator zawiera opcje opóźnienia załadować biblioteki DLL, dopóki program wywołuje funkcję w tej bibliotece DLL.  
  
 Aplikacji można opóźnić ładowania biblioteki DLL przy użyciu [/delayload (opóźnienie załadować Import)](../../build/reference/delayload-delay-load-import.md) — opcja konsolidatora z funkcji pomocniczej (Domyślna implementacja podał Visual C++). Funkcja pomocnika załaduje biblioteki DLL w czasie wykonywania przez wywołanie metody **LoadLibrary** i **GetProcAddress** dla Ciebie.  
  
 Należy rozważyć opóźnienie podczas ładowania biblioteki DLL, jeśli:  
  
-   Program nie może wywołać funkcję w bibliotece DLL.  
  
-   Dopóki w wykonanie programu nie uzyskać wywołać funkcji w bibliotece DLL.  
  
 Opóźnione ładowanie bibliotek DLL może być określony podczas kompilowania albo. Wywołanie pliku EXE lub. Projekt biblioteki DLL. A. Projektu biblioteki DLL, który wybrano opcję opóźnienia ładowania biblioteki DLL co najmniej jeden nie sam wywołać punktu wejścia ładowanych z opóźnieniem w funkcji Dllmain.  
  
 Opóźniaj ładowanie bibliotek DLL można znaleźć w następujących tematach:  
  
-   [Określanie bibliotek DLL w celu opóźnienia ładowania](../../build/reference/specifying-dlls-to-delay-load.md)  
  
-   [Jawne zwalnianie bibliotek DLL załadowanych z opóźnieniem](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md)  
  
-   [Importy Załaduj wszystko dla bibliotek DLL załadowanych z opóźnieniem](../../build/reference/loading-all-imports-for-a-delay-loaded-dll.md)  
  
-   [Powiązywanie importów](../../build/reference/binding-imports.md)  
  
-   [Obsługa błędów oraz powiadomienia](../../build/reference/error-handling-and-notification.md)  
  
-   [Zrzucanie importów załadowanych z opóźnieniem](../../build/reference/dumping-delay-loaded-imports.md)  
  
-   [Ograniczenia bibliotek DLL ładowanych z opóźnieniem](../../build/reference/constraints-of-delay-loading-dlls.md)  
  
-   [Ogólne informacje funkcji Pomocnik](understanding-the-helper-function.md)  
  
-   [Tworzenie własnej funkcji Pomocnik](../../build/reference/developing-your-own-helper-function.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteki dll w programie Visual C++](../../build/dlls-in-visual-cpp.md)   
 [Konsolidacja](../../build/reference/linking.md)