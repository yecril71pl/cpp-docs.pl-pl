---
title: Zwalnianie bibliotek DLL ładowanych z opóźnieniem | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 6463bc71-020e-4aff-a4ca-90360411c54e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fa7b9652c37b6c4e841a798dae3cfeb69779b5ff
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719930"
---
# <a name="unloading-a-delay-loaded-dll"></a>Zwalnianie bibliotek DLL załadowanych z opóźnieniem

Pomocnik dostarczone przez domyślne załadować z opóźnieniem sprawdza, czy deskryptory opóźnionego ładowania mają wskaźnik i kopii oryginalnej tabeli adresów importowania (IAT) w polu pUnloadIAT. Jeśli tak, zostanie ono zapisane wskaźnik na liście importu deskryptora opóźnienia. Dzięki temu funkcja pomocnika odnaleźć biblioteki DLL według nazwy do obsługi jawne zwalnianie tej biblioteki DLL.

Poniżej przedstawiono skojarzone struktur i funkcji dla jawne zwalnianie bibliotek DLL ładowanych z opóźnieniem:

```cpp
//
// Unload support from delayimp.h
//

// routine definition; takes a pointer to a name to unload

ExternC
BOOL WINAPI
__FUnloadDelayLoadedDLL2(LPCSTR szDll);

// structure definitions for the list of unload records
typedef struct UnloadInfo * PUnloadInfo;
typedef struct UnloadInfo {
    PUnloadInfo     puiNext;
    PCImgDelayDescr pidd;
    } UnloadInfo;

// from delayhlp.cpp
// the default delay load helper places the unloadinfo records in the
// list headed by the following pointer.
ExternC
PUnloadInfo __puiHead;
```

Struktura UnloadInfo jest implementowany przy użyciu klasy języka C++, który używa **Funkcja LocalAlloc** i **LocalFree** implementacji jako jego operatora **nowe** i operator  **Usuń** odpowiednio. Te opcje są przechowywane w standardowych połączonej listy przy użyciu __puiHead jako nagłówek listy.

Wywoływanie __FUnloadDelayLoadedDLL spróbuje znaleźć nazwę zapewniają na liście ładowanych bibliotek DLL (wymagana jest dokładne dopasowanie). Jeśli znaleziono kopię IAT w pUnloadIAT są kopiowane w górnej części uruchomionej IAT do przywrócenia wskaźniki thunk, biblioteka zostanie zwolniony z **FreeLibrary**, dopasowywania **UnloadInfo** rekordu jest rozłączony z listy i usunięty, a wartość TRUE jest zwracana.

Argument __FUnloadDelayLoadedDLL2 funkcja jest uwzględniana wielkość liter. Na przykład należy określić:

```cpp
__FUnloadDelayLoadedDLL2("user32.DLL");
```

a nie:

```cpp
__FUnloadDelayLoadedDLL2("User32.DLL");.
```

## <a name="see-also"></a>Zobacz też

[Ogólne informacje funkcji Pomocnik](understanding-the-helper-function.md)