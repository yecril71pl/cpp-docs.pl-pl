---
title: Obliczanie niezbędnych wartości
ms.date: 11/04/2016
helpviewer_keywords:
- helper functions, calculating necessary values
ms.assetid: 4f037d0f-881a-4a48-a9d2-9f8872dfccb7
ms.openlocfilehash: 75952bbcdf823aa675b35702841c81e511105ca8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272653"
---
# <a name="calculating-necessary-values"></a>Obliczanie niezbędnych wartości

Dwa najistotniejsze informacje konieczne jest obliczana przez procedury pomocnika opóźnienia. W tym celu istnieją dwie funkcje wbudowane w delayhlp.cpp do obliczania tych informacji.

- Pierwszy oblicza Indeks bieżącej importowania do trzech różnych tabelach (Importowanie tabeli adresów (IAT), tabeli adresów importowania powiązanego (BIAT) i tabeli adresów importowania niepowiązanych (UIAT)).

- Drugi zlicza Importy w IAT prawidłowe.

```cpp
// utility function for calculating the index of the current import
// for all the tables (INT, BIAT, UIAT, and IAT).
__inline unsigned
IndexFromPImgThunkData(PCImgThunkData pitdCur, PCImgThunkData pitdBase) {
    return pitdCur - pitdBase;
    }

// utility function for calculating the count of imports given the base
// of the IAT. NB: this only works on a valid IAT!
__inline unsigned
CountOfImports(PCImgThunkData pitdBase) {
    unsigned        cRet = 0;
    PCImgThunkData  pitd = pitdBase;
    while (pitd->u1.Function) {
        pitd++;
        cRet++;
        }
    return cRet;
    }
```

## <a name="see-also"></a>Zobacz także

[Ogólne informacje funkcji Pomocnik](understanding-the-helper-function.md)
