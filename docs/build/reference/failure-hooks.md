---
title: Punkty zaczepienia błędów
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, failure hooks
ms.assetid: 12bb303b-ffe6-4471-bffe-9ef4f8bb2d30
ms.openlocfilehash: 2bda1d34c85b1e88c7d278816e30e76537a7523b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463613"
---
# <a name="failure-hooks"></a>Punkty zaczepienia błędów

Punkt zaczepienia błędów jest włączone w taki sam sposób jak [punktu zaczepienia powiadomień](../../build/reference/notification-hooks.md). Nadal musi rutynowych hook wróć odpowiednią wartość przetwarzania (HINSTANCE lub FARPROC) lub 0, aby wskazać, że należy zgłosić wyjątek.

Zmiennej wskaźnika, który odwołuje się do funkcji zdefiniowanej przez użytkownika jest:

```
// This is the failure hook, dliNotify = {dliFailLoadLib|dliFailGetProc}
ExternC
PfnDliHook   __pfnDliFailureHook2;
```

**DelayLoadInfo** struktura zawiera odpowiednie dane konieczne do dokładnego raportowania błędów, z uwzględnieniem wartości z `GetLastError`.

Jeśli powiadomienie jest **dliFailLoadLib**, funkcja podłączania może zwrócić:

- 0, jeśli aplikacja nie może obsłużyć błąd.

- HMODULE, jeśli hook awarii problem został rozwiązany i załadowany sama biblioteka.

Jeśli powiadomienie jest **dliFailGetProc**, funkcja podłączania może zwrócić:

- 0, jeśli aplikacja nie może obsłużyć błąd.

- Proc prawidłowy adres (importu funkcji), jeśli dołączyć awarii powiodło się pobieranie sam adres.

## <a name="see-also"></a>Zobacz też

[Obsługa błędów oraz powiadomienia](../../build/reference/error-handling-and-notification.md)