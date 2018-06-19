---
title: Punkty zaczepienia powiadomień | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- delayed loading of DLLs, notification hooks
ms.assetid: e9c291ed-2f2d-4319-a171-09800625256f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0210c4ee058694594893a029789442c89003da2e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377822"
---
# <a name="notification-hooks"></a>Punkty zaczepienia powiadomień
Punkty zaczepienia powiadomień są nazywane tuż przed w procedurze pomocnika podejmowane są następujące akcje:  
  
-   Dojście przechowywanych w bibliotece jest sprawdzana jeśli jego został już załadowany.  
  
-   **LoadLibrary** jest nazywany próby ładowania biblioteki dll.  
  
-   **GetProcAddress** jest wywoływana, aby podjąć próbę uzyskania adresu procedury.  
  
-   Wróć do thunk obciążenia importu opóźnienia.  
  
 Włączono punktu zaczepienia powiadomień:  
  
-   Podając nową definicję wskaźnika **__pfnDliNotifyHook2** którego zainicjowano wskaż własnej funkcji, która odbiera powiadomienia.  
  
     —lub—  
  
-   Ustawiając kursor **__pfnDliNotifyHook2** do funkcji punktów zaczepienia przed wszystkie wywołania do biblioteki DLL, która jest program opóźnić ładowania.  
  
 Jeśli powiadomienie jest **dliStartProcessing**, funkcja może zwrócić:  
  
 NULL  
 Pomocnik domyślne obsługuje ładowanie biblioteki dll. Dzięki takiemu grupowaniu można wywołać tylko w celach informacyjnych.  
  
 wskaźnik funkcji  
 Pominąć domyślna obsługa załadować z opóźnieniem. Dzięki temu można podać własne obsługi obciążenia.  
  
 Jeśli powiadomienie jest **dliNotePreLoadLibrary**, funkcja może zwrócić:  
  
-   0, po prostu chce powiadomienia informacyjne.  
  
-   Wartość HMODULE załadować biblioteki dll, jeśli go załadować samego biblioteki DLL.  
  
 Jeśli powiadomienie jest **dliNotePreGetProcAddress**, funkcja może zwrócić:  
  
-   0, po prostu chce powiadomienia informacyjne.  
  
-   Adres funkcji zaimportowane, jeśli funkcja pobiera adres.  
  
 Jeśli powiadomienie jest **dliNoteEndProcessing**, funkcji punktów zaczepienia wartość zwracana jest ignorowana.  
  
 Jeśli ten wskaźnik został zainicjowany (różną od zera), pomocnika obciążenia opóźnienie spowoduje wywołanie funkcji w niektórych punktach powiadomień w całym jej wykonanie. Wskaźnik funkcji ma następującą definicję:  
  
```  
// The "notify hook" gets called for every call to the  
// delay load helper.  This allows a user to hook every call and  
// skip the delay load helper entirely.  
//  
// dliNotify == {  
//  dliStartProcessing |  
//  dliNotePreLoadLibrary  |  
//  dliNotePreGetProc |  
//  dliNoteEndProcessing}  
//  on this call.  
//  
ExternC  
PfnDliHook   __pfnDliNotifyHook2;  
  
// This is the failure hook, dliNotify = {dliFailLoadLib|dliFailGetProc}  
ExternC  
PfnDliHook   __pfnDliFailureHook2;  
```  
  
 Przekazywanie powiadomień **DelayLoadInfo** struktury funkcji punktów zaczepienia wraz z wartością powiadomień. Te dane są używaną przez procedury pomocnika obciążenia opóźnienia. Wartość powiadomień będzie jedną z wartości zdefiniowanych w [struktura i stała — definicje](../../build/reference/structure-and-constant-definitions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa błędów oraz powiadomienia](../../build/reference/error-handling-and-notification.md)