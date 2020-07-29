---
title: Zwalnianie bibliotek DLL załadowanych z opóźnieniem
ms.date: 11/04/2016
helpviewer_keywords:
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 6463bc71-020e-4aff-a4ca-90360411c54e
ms.openlocfilehash: 1895bf12cb195ef7b4555d400badf112d377547b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211921"
---
# <a name="unloading-a-delay-loaded-dll"></a>Zwalnianie bibliotek DLL załadowanych z opóźnieniem

Domyślne, dostarczone przez program pomocnika ładowania opóźnień, aby sprawdzić, czy deskryptory ładowania opóźnień mają wskaźnik i kopię oryginalnej tabeli adresów importu (IAT) w polu pUnloadIAT. Jeśli tak, zostanie zapisany wskaźnik na liście do deskryptora opóźnienia importu. Umożliwia to funkcji pomocnika znalezienie biblioteki DLL według nazwy do obsługi wyładowania biblioteki DLL jawnie.

Poniżej przedstawiono skojarzone struktury i funkcje w celu jawnego wyładowania biblioteki DLL załadowanej z opóźnieniem:

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

Struktura UnloadInfo jest implementowana przy użyciu klasy języka C++, która korzysta odpowiednio z implementacji **LocalAlloc** i **LocalFree** jako operatora **`new`** i operatora **`delete`** . Te opcje są przechowywane na standardowej liście połączonej przy użyciu __puiHead jako nagłówka listy.

Wywołanie __FUnloadDelayLoadedDLL podejmie próbę znalezienia podania nazwy na liście załadowanych bibliotek DLL (wymagane jest dokładne dopasowanie). W przypadku znalezienia kopia IAT w pUnloadIAT jest kopiowana na początku uruchomionego IAT w celu przywrócenia wskaźników thunk, biblioteka jest zwolniona z **FreeLibrary**, pasujący rekord **UnloadInfo** jest odłączany od listy i usunięty, a wartość true jest zwracana.

Argument funkcji __FUnloadDelayLoadedDLL2 uwzględnia wielkość liter. Na przykład należy określić:

```cpp
__FUnloadDelayLoadedDLL2("user32.DLL");
```

i nie:

```cpp
__FUnloadDelayLoadedDLL2("User32.DLL");.
```

## <a name="see-also"></a>Zobacz także

[Zrozumienie funkcji pomocnika](understanding-the-helper-function.md)
