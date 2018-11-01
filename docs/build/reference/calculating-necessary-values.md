---
title: Obliczanie niezbędnych wartości
ms.date: 11/04/2016
helpviewer_keywords:
- helper functions, calculating necessary values
ms.assetid: 4f037d0f-881a-4a48-a9d2-9f8872dfccb7
ms.openlocfilehash: 80c028a315669fb0032628bb86a834d429935f50
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50513870"
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

## <a name="see-also"></a>Zobacz też

[Ogólne informacje funkcji Pomocnik](understanding-the-helper-function.md)