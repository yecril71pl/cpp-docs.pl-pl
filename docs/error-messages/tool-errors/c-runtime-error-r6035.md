---
title: Błąd czasu wykonania języka C R6035
ms.date: 11/04/2016
f1_keywords:
- R6035
helpviewer_keywords:
- R6035
ms.assetid: f8fb50b8-18bf-4258-b96a-b0a9de468d16
ms.openlocfilehash: 9b92b1e2e123201d4f50422754b77f62b2ec943b
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404401"
---
# <a name="c-runtime-error-r6035"></a>Błąd czasu wykonania języka C R6035

Microsoft Visual C++ biblioteki środowiska uruchomieniowego, błąd R6035 — moduł w tej aplikacji inicjuje globalny plik cookie zabezpieczeń modułu, podczas gdy funkcja polegające na tym pliku cookie zabezpieczeń jest aktywna.  Wywołaj __security_init_cookie wcześniej.

[__security_init_cookie](../../c-runtime-library/reference/security-init-cookie.md) musi zostać wywołana przed pierwszym użyciem globalnego pliku cookie zabezpieczeń.

Globalny plik cookie zabezpieczeń jest używany na potrzeby ochrony przepełnienia buforu w kodzie skompilowanym za pomocą [/GS (sprawdzanie zabezpieczeń bufora)](../../build/reference/gs-buffer-security-check.md) i w kodzie, który używa obsługi wyjątków strukturalnych. Zasadniczo przy wejściu do funkcji chronionej przez przepełnienie plik cookie jest umieszczany na stosie, a po zakończeniu wartość na stosie jest porównywana z globalnym plikiem cookie. Każda różnica między nimi wskazuje, że przepełnienie buforu nastąpiło i powoduje natychmiastowe zakończenie działania programu.

R6035 błędów wskazuje, że wywołanie `__security_init_cookie` zostało wykonane po wprowadzeniu chronionej funkcji. Jeśli wykonanie było kontynuowane, zostanie wykryte przepełnienie bufora fałszywe, ponieważ plik cookie na stosie nie jest już zgodny z globalnym plikiem cookie.

Rozważmy następujący przykład biblioteki DLL. Punkt wejścia biblioteki DLL jest ustawiany na DllEntryPoint za pomocą opcji konsolidatora [/entry (symbol punktu wejścia)](../../build/reference/entry-entry-point-symbol.md) . Pomija to inicjalizację CRT, która zwykle inicjuje globalną ochronę pliku cookie, dlatego sama Biblioteka DLL musi wywołać `__security_init_cookie` .

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

Ten przykład generuje błąd R6035, ponieważ DllEntryPoint używa obsługi wyjątków strukturalnych, w związku z czym używa pliku cookie zabezpieczeń do wykrywania przepełnień buforu. Gdy DllInitialize jest wywoływana, plik cookie zabezpieczeń globalnych został już umieszczony na stosie.

Prawidłowy sposób przedstawiono w tym przykładzie:

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

W takim przypadku DllEntryPoint nie jest chroniony przed przekroczeniem buforu (nie ma on lokalnych buforów ciągów i nie używa obsługi wyjątków strukturalnych); w związku z tym może bezpiecznie wywołać `__security_init_cookie` . Następnie wywołuje funkcję pomocnika, która jest chroniona.

> [!NOTE]
> Komunikat o błędzie R6035 jest generowany tylko przez CRT debugowania x86 i tylko dla obsługi wyjątków strukturalnych, ale warunek jest błędem na wszystkich platformach i dla wszystkich form obsługi wyjątków, takich jak C++ EH.

## <a name="see-also"></a>Zobacz też

[Funkcje zabezpieczeń w programie MSVC](https://devblogs.microsoft.com/cppblog/security-features-in-microsoft-visual-c/)
