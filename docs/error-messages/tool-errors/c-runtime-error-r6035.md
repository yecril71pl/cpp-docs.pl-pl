---
title: "Po R6035 błąd w czasie wykonywania C | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- R6035
dev_langs:
- C++
helpviewer_keywords:
- R6035
ms.assetid: f8fb50b8-18bf-4258-b96a-b0a9de468d16
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6b5f9fb1f7562b26382c6b36e3947367013631bf
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="c-runtime-error-r6035"></a>Po R6035 błąd w czasie wykonywania C
Biblioteka programu Microsoft Visual C++ środowiska wykonawczego, po R6035 błąd - module w tej aplikacji jest podczas inicjowania pliku cookie zabezpieczeń globalnych modułu, gdy funkcja polegania na ten plik cookie zabezpieczeń jest aktywny.  Wywołanie __security_init_cookie — wcześniej.  
  
 [__security_init_cookie —](../../c-runtime-library/reference/security-init-cookie.md) musi zostać wywołana przed pierwszym użyciem plik cookie zabezpieczeń globalnych.  
  
 Plik cookie zabezpieczeń globalnych służy do ochrony przepełnienie buforu w kodzie skompilowanym z [/GS (Sprawdzanie zabezpieczeń bufora)](../../build/reference/gs-buffer-security-check.md) i w kodzie, który używa Obsługa wyjątków strukturalnych. Zasadniczo przy wejściu do funkcji chronionych przekroczenie, plik cookie jest umieszczany na stosie, a po zakończeniu wartość na stosie jest porównywana globalnego pliku cookie. Różnicę między nimi wskazuje, czy nastąpiło przepełnienie buforu oraz powoduje natychmiastowe przerwanie działania programu.  
  
 Po R6035 błąd wskazuje, że wywołanie `__security_init_cookie` został utworzony po wprowadzono funkcję chronionych. Jeżeli kontynuować wykonywania, przepełnienie buforu fałszywe można wykryć ponieważ plik cookie na stosie nie spowoduje dopasowanie globalnego pliku cookie.  
  
 Należy wziąć pod uwagę w poniższym przykładzie biblioteki DLL. Punkt wejścia biblioteki DLL ma ustawioną wartość DllEntryPoint przez konsolidator [/Entry (Symbol punktu wejścia)](../../build/reference/entry-entry-point-symbol.md) opcji. To powoduje pominięcie inicjowania CRT, które zwykle może ustawić plik cookie zabezpieczeń globalnych, tak się biblioteki DLL należy wywołać metodę `__security_init_cookie`.  
  
```  
// Wrong way to call __security_init_cookie  
DllEntryPoint(...) {  
   DllInitialize();  
   ...  
   __try {  
      ...  
   } __except()... {  
      ...  
   }  
}  
  
void DllInitialize() {  
   __security_init_cookie();  
}  
```  
  
 W tym przykładzie wygeneruje błąd po R6035, ponieważ DllEntryPoint używa Obsługa wyjątków strukturalnych i w związku z tym używa pliku cookie zabezpieczeń do wykrywania przepełnienia buforu. W czasie, gdy zostanie wywołana DllInitialize plik cookie zabezpieczeń globalnych ma już wprowadzone na stosie.  
  
 Prawidłowy sposób przedstawionej w tym przykładzie:  
  
```  
// Correct way to call __security_init_cookie  
DllEntryPoint(...) {  
   __security_init_cookie();  
   DllEntryHelper();  
}  
  
void DllEntryHelper() {  
   ...  
   __try {  
      ...  
   } __except()... {  
      ...  
   }  
}  
```  
  
 W takim przypadku DllEntryPoint nie jest chroniony przed przepełnienia buforu (ma buforów ciąg lokalnym i nie używa Obsługa wyjątków strukturalnych;) w związku z tym można bezpiecznie wywołać `__security_init_cookie`. Następnie wywołuje funkcję pomocnika, która jest chroniona.  
  
> [!NOTE]
>  Komunikat o błędzie, który jest po R6035 tylko wygenerowane przez x86 debugowania CRT i tylko w przypadku obsługa wyjątków strukturalnych, ale warunku błędu na wszystkich platformach i dla wszystkich formularzy wyjątku obsługuje, takich jak C++ EH.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrole zabezpieczeń kompilatora szczegółowo](http://go.microsoft.com/fwlink/p/?linkid=7260)