---
title: -STACK — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /stack
dev_langs:
- C++
helpviewer_keywords:
- -STACK editbin option
- STACK editbin option
- stack, setting size
- /STACK editbin option
ms.assetid: a39bcff0-c945-4355-80cc-8e4f24a5f142
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d8deb3e3bedcb773aa01ae5f1c3ff66ce9d509f2
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716669"
---
# <a name="stack"></a>/STACK

```
/STACK:reserve[,commit]
```

## <a name="remarks"></a>Uwagi

Ta opcja ustawia rozmiar stosu w bajtach i przyjmuje argumenty w notacji dziesiętnej lub języka C. Opcja /STACK ma zastosowanie tylko do pliku wykonywalnego.

*Zarezerwować* argument określa Alokacja całkowita stosu w pamięci wirtualnej. EDITBIN zaokrągla w górę określoną wartość do najbliższej 4 bajty.

Opcjonalny `commit` argument podlega interpretacji przez system operacyjny. Windows NT, Windows 95 i Windows 98 `commit` określa ilość pamięci fizycznej do przydzielenia w danym momencie. Zadeklarowanej pamięci wirtualnej powoduje, że miejsce, które mają zostać zarezerwowane w pliku stronicowania. Uzyskanie lepszej `commit` wartość pozwala zaoszczędzić czas, gdy potrzeba więcej miejsca na stosie aplikacji, ale zwiększa wymagania dotyczące pamięci i ewentualnie czas uruchamiania.

## <a name="see-also"></a>Zobacz też

[Opcje EDITBIN](../../build/reference/editbin-options.md)