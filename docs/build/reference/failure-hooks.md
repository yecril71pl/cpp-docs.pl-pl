---
title: Punkty zaczepienia błędów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- delayed loading of DLLs, failure hooks
ms.assetid: 12bb303b-ffe6-4471-bffe-9ef4f8bb2d30
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: be598a77ca48eeee03360a3b598b0567abc6ee4b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371788"
---
# <a name="failure-hooks"></a>Punkty zaczepienia błędów
Haku błędu jest włączone w taki sam sposób jak [punktu zaczepienia powiadomień](../../build/reference/notification-hooks.md). Kontynuować musi rutynowych haku zwraca odpowiednie wartości tak, aby przetwarzania (wystąpienie HINSTANCE lub FARPROC) lub wpisz 0, aby wskazać, że zgłaszany wyjątek.  
  
 Jest zmienna wskaźnika, która odwołuje się do funkcji zdefiniowanej przez użytkownika:  
  
```  
// This is the failure hook, dliNotify = {dliFailLoadLib|dliFailGetProc}  
ExternC  
PfnDliHook   __pfnDliFailureHook2;  
```  
  
 **DelayLoadInfo** struktura zawiera istotne dane niezbędne do dokładnych raportowania błędów, z uwzględnieniem wartości z `GetLastError`.  
  
 Jeśli powiadomienie jest **dliFailLoadLib**, funkcja może zwrócić:  
  
-   0, jeśli nie można obsłużyć awarię.  
  
-   HMODULE, jeśli haku awarii problem został rozwiązany i załadować samej biblioteki.  
  
 Jeśli powiadomienie jest **dliFailGetProc**, funkcja może zwrócić:  
  
-   0, jeśli nie można obsłużyć awarię.  
  
-   Proc prawidłowy adres (importu funkcji), jeśli utworzenie punktu zaczepienia awarii powiodło się pobieranie adres.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa błędów oraz powiadomienia](../../build/reference/error-handling-and-notification.md)