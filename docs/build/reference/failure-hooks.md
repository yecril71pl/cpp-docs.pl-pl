---
title: "Punkty zaczepienia błędów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: delayed loading of DLLs, failure hooks
ms.assetid: 12bb303b-ffe6-4471-bffe-9ef4f8bb2d30
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1609b713fef253e8beab270ee2ed048466da6504
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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