---
title: Obliczanie niezbędnych wartości | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- helper functions, calculating necessary values
ms.assetid: 4f037d0f-881a-4a48-a9d2-9f8872dfccb7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e56acaecd038b7580423e078459e39994391052a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722361"
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