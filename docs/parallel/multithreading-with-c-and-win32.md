---
title: "Wielowątkowość z C i Win32 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Windows API [C++], multithreading
- multithreading [C++], C and Win32
- Visual C, multithreading
- Win32 applications [C++], multithreading
- threading [C++], C and Win32
- Win32 [C++], multithreading
- threading [C]
ms.assetid: 67cdc99e-1ad9-452b-a042-ed246b70040e
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 30c7833a4df80669b6223f1fe6b1ccceed0257cc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="multithreading-with-c-and-win32"></a>Wielowątkowość z językiem C i podsystemem Win32
Microsoft Visual C++ zapewnia obsługę tworzenia wielowątkowe aplikacje w systemie Microsoft Windows: Windows XP, Windows 2000, Windows NT, Windows Me i Windows 98. Należy rozważyć użycie więcej niż jeden wątek, jeśli aplikacja musi zarządzać wielu działań, takich jak jednoczesnych klawiatury i myszy. Jeden wątek może przetwarzać danych wprowadzonych z klawiatury, gdy drugi wątek filtry działania myszy. Trzeci wątku można aktualizować ekranu na podstawie danych z wątków myszy i klawiatury. W tym samym czasie inne wątki można uzyskać dostęp do plików dysku lub Pobierz dane z portem komunikacyjnym.  
  
 Z programem Visual C++, istnieją dwa sposoby do programu z wielu wątków: za pomocą biblioteki Microsoft Foundation Class (MFC) lub biblioteki wykonawczej języka C i Win32 API. Aby uzyskać informacje o tworzeniu aplikacji wielowątkowe z MFC, zobacz [Multithreading z C++ i MFC](../parallel/multithreading-with-cpp-and-mfc.md) zapoznanie się z następujących tematów dotyczących multithreading c.  
  
 Te tematy wyjaśniają funkcji w programie Visual C++, które obsługują tworzenie programy wielowątkowe.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
  
-   [Co wielowątkowość dotyczy](../parallel/multithread-programs.md)  
  
-   [Obsługa bibliotek na potrzeby wielowątkowości](../parallel/library-support-for-multithreading.md)  
  
-   [Dołącz pliki dla wielowątkowości](../parallel/include-files-for-multithreading.md)  
  
-   [Funkcje bibliotek C-Run-Time do sterowania wątkami](../parallel/c-run-time-library-functions-for-thread-control.md)  
  
-   [Przykładowy program wielowątkowe w języku C](../parallel/sample-multithread-c-program.md)  
  
-   [Pisanie programu systemu Win32 wielowątkowe](../parallel/writing-a-multithreaded-win32-program.md)  
  
-   [Kompilowanie i łączenie programów wielowątkowych](../parallel/compiling-and-linking-multithread-programs.md)  
  
-   [Unikanie obszarów problemów z programami wielowątkowymi](../parallel/avoiding-problem-areas-with-multithread-programs.md)  
  
-   [Lokalny magazyn wątków (TLS)](../parallel/thread-local-storage-tls.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wielowątkowości w przypadku starszego kodu (Visual C++)](../parallel/multithreading-support-for-older-code-visual-cpp.md)