---
title: R6035 błąd środowiska uruchomieniowego języka C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6035
dev_langs:
- C++
helpviewer_keywords:
- R6035
ms.assetid: f8fb50b8-18bf-4258-b96a-b0a9de468d16
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 081e878e6bc96edc734f84e0e4efecee607135b5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026716"
---
# <a name="c-runtime-error-r6035"></a>R6035 błąd środowiska uruchomieniowego języka C

Biblioteki Microsoft Visual C++ środowiska uruchomieniowego, R6035 błąd - module w tej aplikacji Trwa inicjowanie plik cookie zabezpieczeń globalnych modułu w czasie gdy aktywny jest funkcją, opierając się na ten plik cookie zabezpieczeń.  Wywołaj __security_init_cookie wcześniej.

[__security_init_cookie](../../c-runtime-library/reference/security-init-cookie.md) musi zostać wywołana przed pierwszym użyciem plik cookie zabezpieczeń globalnych.

Plik cookie zabezpieczeń globalnych służy do ochrony przepełnienie buforu w kodzie skompilowanym z [/GS (Sprawdzanie zabezpieczeń bufora)](../../build/reference/gs-buffer-security-check.md) i w kodzie, który używa strukturalna Obsługa wyjątków. Zasadniczo przy wejściu do funkcji chronionych przekroczenie, plik cookie jest umieszczany na stosie, a przy zamykaniu, wartość na stosie jest porównywana globalnego pliku cookie. Wszelkie różnice między nimi wskazuje, że przepełnienie buforu wystąpił i powoduje natychmiastowe przerwanie działania programu.

R6035 błąd wskazuje, że wywołanie `__security_init_cookie` został utworzony po wprowadzono funkcję chronionych. Gdyby kontynuować wykonywanie, przepełnienie buforu fałszywe będzie wykryła, ponieważ plik cookie na stosie już nie będzie odpowiadać globalnego pliku cookie.

Rozważmy następujący przykład biblioteki DLL. Punkt wejścia biblioteki DLL jest równa DllEntryPoint za pośrednictwem konsolidatora [/Entry (Symbol punktu wejścia)](../../build/reference/entry-entry-point-symbol.md) opcji. Pomija to Inicjalizacja CRT, który zazwyczaj będzie zainicjować plik cookie zabezpieczeń globalnych, więc wywołania biblioteki DLL, sama `__security_init_cookie`.

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

Ten przykład wygeneruje błąd R6035, ponieważ DllEntryPoint używa strukturalna Obsługa wyjątków i w związku z tym używa pliku cookie zabezpieczeń do wykrywania przepełnienia buforu. Przez razem, gdy jest wywoływana DllInitialize plik cookie zabezpieczeń globalnych już została wprowadzona na stosie.

Prawidłowy sposób została przedstawiona w tym przykładzie:

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

W tym przypadku DllEntryPoint nie są chronione przed przepełnienia buforu (go ma buforów ciągu lokalne i nie używa strukturalna Obsługa wyjątków); w związku z tym można bezpiecznie wywołać `__security_init_cookie`. Następnie wywołuje funkcję pomocnika, która jest chroniona.

> [!NOTE]
>  Komunikat o błędzie, który jest R6035 tylko generowane przez x86 debugowania CRT i tylko w przypadku strukturalna Obsługa wyjątków, ale ten stan jest na wszystkich platformach i dla wszystkich formularzy wyjątek obsługę błędów, takich jak EH w języku C++.

## <a name="see-also"></a>Zobacz też

[Funkcje zabezpieczeń w MSVC](https://blogs.msdn.microsoft.com/vcblog/2017/06/28/security-features-in-microsoft-visual-c/)