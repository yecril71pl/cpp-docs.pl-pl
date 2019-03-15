---
title: Punkty zaczepienia błędów
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, failure hooks
ms.assetid: 12bb303b-ffe6-4471-bffe-9ef4f8bb2d30
ms.openlocfilehash: 2fc22ae77d729868adbf8c37d40e450e35a8e866
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811995"
---
# <a name="failure-hooks"></a>Punkty zaczepienia błędów

Punkt zaczepienia błędów jest włączone w taki sam sposób jak [punktu zaczepienia powiadomień](notification-hooks.md). Nadal musi rutynowych hook wróć odpowiednią wartość przetwarzania (HINSTANCE lub FARPROC) lub 0, aby wskazać, że należy zgłosić wyjątek.

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

## <a name="see-also"></a>Zobacz także

[Obsługa błędów oraz powiadomienia](error-handling-and-notification.md)
