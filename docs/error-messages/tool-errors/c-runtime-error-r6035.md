---
title: Błąd czasu wykonania języka C R6035
ms.date: 11/04/2016
f1_keywords:
- R6035
helpviewer_keywords:
- R6035
ms.assetid: f8fb50b8-18bf-4258-b96a-b0a9de468d16
ms.openlocfilehash: ff3cd0259df92aa5cdade3f78a240e69f8f6f7de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377476"
---
# <a name="c-runtime-error-r6035"></a>Błąd czasu wykonania języka C R6035

Biblioteka środowiska wykonawczego Microsoft Visual C++, błąd R6035 — moduł w tej aplikacji inicjuje globalny plik cookie zabezpieczeń modułu, podczas gdy funkcja polegająca na tym pliku cookie zabezpieczeń jest aktywna.  Zadzwoń __security_init_cookie wcześniej.

[__security_init_cookie](../../c-runtime-library/reference/security-init-cookie.md) musi zostać wywołana przed pierwszym użyciem globalnego pliku cookie zabezpieczeń.

Globalny plik cookie zabezpieczeń jest używany do ochrony przepełnienia buforu w kodzie skompilowanym za pomocą [/GS (Kontrola zabezpieczeń bufora)](../../build/reference/gs-buffer-security-check.md) i w kodzie, który używa obsługi wyjątków strukturalnych. Zasadniczo przy wejściu do funkcji chronionej przed przekroczeniem plik cookie jest umieszczany na stosie, a po wyjściu wartość na stosie jest porównywana z globalnym plikiem cookie. Wszelkie różnice między nimi wskazuje, że doszło do przekroczenia buforu i powoduje natychmiastowe zakończenie programu.

Błąd R6035 wskazuje, że `__security_init_cookie` wywołanie zostało wykonane po wprowadzeniu chronionej funkcji. Jeśli wykonanie miałoby być kontynuowane, zostanie wykryte przekroczenie fałszywego buforu, ponieważ plik cookie na stosie nie będzie już zgodny z globalnym plikiem cookie.

Rozważmy poniższy przykład biblioteki DLL. Punkt wejścia biblioteki DLL jest ustawiony na DllEntryPoint za pomocą konsolidatora [/ENTRY (Entry-Point Symbol).](../../build/reference/entry-entry-point-symbol.md) Pomija to inicjalizację CRT, która zwykle inicjuje globalny plik cookie zabezpieczeń, więc sama biblioteka DLL musi wywołać `__security_init_cookie`.

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

W tym przykładzie wygeneruje błąd R6035, ponieważ DllEntryPoint używa obsługi wyjątków strukturalnych i dlatego używa pliku cookie zabezpieczeń do wykrywania przepełnień buforu. Do czasu DllInitialize jest wywoływana, globalny plik cookie zabezpieczeń został już umieszczony na stosie.

Prawidłowy sposób jest pokazany w tym przykładzie:

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

W takim przypadku DllEntryPoint nie jest chroniony przed przekroczeniem buforu (nie ma buforów ciągów lokalnych i nie używa obsługi wyjątków strukturalnych); dlatego może bezpiecznie `__security_init_cookie`zadzwonić . Następnie wywołuje funkcję pomocnika, która jest chroniona.

> [!NOTE]
> Komunikat o błędzie R6035 jest generowany tylko przez x86 debug CRT i tylko dla obsługi wyjątków strukturalnych, ale warunek jest błąd na wszystkich platformach i dla wszystkich form obsługi wyjątków, takich jak C++ EH.

## <a name="see-also"></a>Zobacz też

[Funkcje zabezpieczeń w msvc](https://blogs.msdn.microsoft.com/vcblog/2017/06/28/security-features-in-microsoft-visual-c/)
