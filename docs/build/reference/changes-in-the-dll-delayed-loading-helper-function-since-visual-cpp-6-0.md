---
title: "Zmiany w bibliotece DLL funkcjach pomocnika opóźnionego załadunku po Visual C++ 6.0 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- delayed loading of DLLs, what's changed
- PFromRva method
- __delayLoadHelper2 function
- helper functions, what's changed
ms.assetid: 99f0be69-105d-49ba-8dd5-3be7939c0c72
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fb16beb6f2ddb07f57fe9f35c67552348cac56cc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="changes-in-the-dll-delayed-loading-helper-function-since-visual-c-60"></a>Zmiany w funkcjach pomocnika opóźnionego załadunku bibliotek DLL po Visual C++ 6.0
Jeśli masz wiele wersji programu Visual C++ na komputerze lub jeśli zdefiniowano własnej funkcji Pomocnik użytkownik może dotyczyć zmian wprowadzonych do biblioteki DLL funkcjach pomocnika opóźnionego załadunku. Na przykład:  
  
-   **__delayloadhelper —** jest teraz **__delayloadhelper2 —**  
  
-   **__pfnDliNotifyHook** jest teraz **__pfnDliNotifyHook2**  
  
-   **__pfnDliFailureHook** jest teraz **__pfnDliFailureHook2**  
  
-   **__FUnloadDelayLoadedDLL** jest teraz **__FUnloadDelayLoadedDLL2**  
  
> [!NOTE]
>  Jeśli korzystasz z domyślnej funkcji pomocnika, te zmiany nie wpływają na należy. Nie wprowadzono żadnych zmian dotyczących sposobu wywołuje konsolidator.  
  
## <a name="multiple-versions-of-visual-c"></a>Wiele wersji programu Visual C++  
 Jeśli masz wiele wersji programu Visual C++ na komputerze, upewnij się, że konsolidator odpowiada delayimp.lib. Jeśli występuje niezgodność, otrzyma albo raportowania błędów konsolidatora `___delayLoadHelper2@8` lub `___delayLoadHelper@8` jako nierozpoznany zewnętrzny symbol. Pierwsza oznacza nowe konsolidatora z starego delayimp.lib, i drugie oznacza starego konsolidatora z nowego delayimp.lib.  
  
 Jeśli wystąpi błąd nierozwiązane konsolidatora Uruchom [dumpbin /linkermember](../../build/reference/linkermember.md): 1 w delayimp.lib, który będzie zawierać sprawdzić funkcji pomocnika jest zdefiniowany w zamian funkcji pomocnika. Funkcja pomocnika można również zdefiniować w pliku obiektu; Uruchom [dumpbin /symbols](../../build/reference/symbols.md) i poszukaj `delayLoadHelper(2)`.  
  
 Jeśli wiesz, że masz konsolidatora Visual C++ 6.0, następnie:  
  
-   Uruchom polecenia dumpbin na pomocnika obciążenia opóźnienie plik .lib lub .obj, aby określić, czy definiuje **__delayloadhelper2 —**. W przeciwnym razie łącze zakończy się niepowodzeniem.  
  
-   Zdefiniuj **__delayloadhelper —** opóźnienie załadować pliku lib lub .obj tego pomocnika.  
  
## <a name="user-defined-helper-function"></a>Funkcja pomocnika zdefiniowanych przez użytkownika  
 Jeśli zdefiniowano własnej funkcji Pomocnik i korzystają z bieżącą wersją programu Visual C++, wykonaj następujące czynności:  
  
-   Zmień nazwę funkcji pomocnika **__delayloadhelper2 —**.  
  
-   Ponieważ wskaźniki w deskryptorze opóźnienie (ImgDelayDescr w delayimp.h) zostały zmienione z adresów bezwzględnych (kanalików) względnych adresów (RVAs) do pracy w oczekiwany sposób w obu programów 32 - i 64-bitowych, należy przekonwertować te wstecz do wskaźników. Wprowadzono nową funkcję: PFromRva w delayhlp.cpp. Aby przekonwertować je albo 32 - lub 64-bitowych wskaźników służy tej funkcji na każde z pól w deskryptorze przestrzeni. Funkcję pomocnicza ładowaną opóźnienie domyślny jest nadal dobrej szablon do użycia jako przykład.  
  
## <a name="load-all-imports-for-a-delay-loaded-dll"></a>Załaduj wszystkie Importy dla biblioteki DLL załadowanych z opóźnieniem  
 Konsolidator może załadować wszystkie Importy z wybraną opóźnienie załadować biblioteki DLL. Zobacz [ładowania wszystkie Importy dla biblioteki DLL Delay-Loaded](../../build/reference/loading-all-imports-for-a-delay-loaded-dll.md) Aby uzyskać więcej informacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Opis funkcji Pomocnik](understanding-the-helper-function.md)