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
ms.openlocfilehash: e4c69759034dbb7233970bd89616a062a369cc13
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721282"
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