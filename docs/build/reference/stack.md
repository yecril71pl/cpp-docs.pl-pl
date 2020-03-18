---
title: /STACK
ms.date: 11/04/2016
f1_keywords:
- /stack_editbin
helpviewer_keywords:
- -STACK editbin option
- STACK editbin option
- stack, setting size
- /STACK editbin option
ms.assetid: a39bcff0-c945-4355-80cc-8e4f24a5f142
ms.openlocfilehash: 63fcddec8ff8afd81084bb5a2786f394db594b07
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438884"
---
# <a name="stack"></a>/STACK

```
/STACK:reserve[,commit]
```

## <a name="remarks"></a>Uwagi

Ta opcja ustawia rozmiar stosu w bajtach i przyjmuje argumenty w notacji dziesiętnej lub w języku C. Opcja/STACK ma zastosowanie tylko do pliku wykonywalnego.

Argument *rezerwy* określa całkowitą alokację stosu w pamięci wirtualnej. POLECENIA EDITBIN zaokrągla określoną wartość do najbliższych 4 bajtów.

Opcjonalny `commit` argument podlega interpretacji przez system operacyjny. W systemie Windows NT, Windows 95 i Windows 98 `commit` określa ilość pamięci fizycznej do przydzielenia w danym momencie. Przydzielona pamięć wirtualna powoduje, że miejsce jest zarezerwowane w pliku stronicowania. Wyższa wartość `commit` umożliwia zaoszczędzenie czasu, gdy aplikacja wymaga większej ilości miejsca w stosie, ale zwiększa wymagania dotyczące pamięci i czas uruchamiania.

## <a name="see-also"></a>Zobacz też

[Opcje EDITBIN](editbin-options.md)
