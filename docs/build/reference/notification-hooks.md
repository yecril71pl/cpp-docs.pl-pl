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
ms.openlocfilehash: 97e471e2de1ecb6ec6664658a2f1c5df09bc8079
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700625"
---
# <a name="notification-hooks"></a>Punkty zaczepienia powiadomień

Punkty zaczepienia powiadomień są wywoływane tuż przed, w procedurze pomocnika podejmowane są następujące akcje:

- Przechowywane uchwyt do biblioteki programu jest sprawdzenie jeśli jego został już załadowany.

- **LoadLibrary** jest wywoływana, aby spróbować obciążenia biblioteki dll.

- **GetProcAddress** jest wywoływana, aby spróbować uzyskać adres procedury.

- Wróć do Opóźnij importowanie ładowania thunk.

Włączono punkt zaczepienia powiadomień:

- Podając nową definicję wskaźnika **__pfnDliNotifyHook2** który jest inicjowany, aby wskazać własną funkcję, która odbiera powiadomienia.

   \-lub —

- Ustawiając kursor **__pfnDliNotifyHook2** do funkcji punktów zaczepienia przed wszelkie wywołania do biblioteki DLL, który program jest opóźnienie ładowania.

Jeśli powiadomienie jest **dliStartProcessing**, funkcja podłączania może zwrócić:

- NULL

   Pomocnik domyślne obsługuje ładowanie biblioteki DLL. Dzięki takiemu grupowaniu można wywoływać tylko dla celów informacyjnych.

- Wskaźnik funkcji

   Pominąć domyślna obsługa załadować z opóźnieniem. Dzięki temu możesz podać własne obsługi obciążenia.

Jeśli powiadomienie jest **dliNotePreLoadLibrary**, funkcja podłączania może zwrócić:

- 0, jeśli tylko powiadomienia informacyjne.

- HMODULE załadować biblioteki dll, jeśli go załadować biblioteki DLL, sam.

Jeśli powiadomienie jest **dliNotePreGetProcAddress**, funkcja podłączania może zwrócić:

- 0, jeśli tylko powiadomienia informacyjne.

- Adres funkcji importowanych, jeśli funkcja podłączania pobiera adres.

Jeśli powiadomienie jest **dliNoteEndProcessing**, funkcja podłączania zwracana wartość jest ignorowana.

Jeśli ten wskaźnik jest zainicjowany (niezerowe), pomocnika obciążenia opóźnienia spowoduje wywołanie funkcji w niektórych punktach powiadomień w całym jej wykonanie. Wskaźnik funkcji ma następującą definicję:

```C
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

Przekaż powiadomienia **DelayLoadInfo** strukturę do funkcji punktów zaczepienia wraz z wartością powiadomień. Te dane są używaną przez procedury pomocnika obciążenia opóźnienia. Wartość powiadomień będzie jedna z wartości zdefiniowanych w [struktura i stała — definicje](../../build/reference/structure-and-constant-definitions.md).

## <a name="see-also"></a>Zobacz też

[Obsługa błędów oraz powiadomienia](../../build/reference/error-handling-and-notification.md)