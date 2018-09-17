---
title: -STERTY | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /heap
dev_langs:
- C++
helpviewer_keywords:
- heap allocation, setting heap size
- HEAP editbin option
- -HEAP editbin option
- /HEAP editbin option
ms.assetid: 6ce759b5-75b7-44ff-a5fd-3a83a0ba9a48
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 22698760ba23dc60b64002f0f728bb7a036f6731
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45699819"
---
# <a name="heap"></a>/HEAP

Ustawia rozmiar stosu w bajtach. Ta opcja dotyczy tylko plików wykonywalnych.

```

/HEAP:
reserve[,commit]
```

## <a name="remarks"></a>Uwagi

`reserve` Argument określa Alokacja łączna liczba początkowa sterty w pamięci wirtualnej. Domyślnie rozmiar stosu jest 1 MB. [Odwołanie EDITBIN](../../build/reference/editbin-reference.md) zaokrągla w górę określoną wartość do najbliższej wielokrotności 4 bajty.

Opcjonalny `commit` argument podlega interpretacji przez system operacyjny. W systemie operacyjnym Windows określa początkowej ilość pamięci fizycznej do przydzielenia, a ilość dodatkowej pamięci do przydzielenia, gdy stos musi być rozwinięty. Zadeklarowanej pamięci wirtualnej powoduje, że miejsce, które mają zostać zarezerwowane w pliku stronicowania. Uzyskanie lepszej `commit` wartość umożliwia systemowi można przydzielić pamięci na mniejsze często, gdy aplikacja potrzebuje więcej miejsca na stercie, ale zwiększa wymagania dotyczące pamięci i ewentualnie czas trwania uruchomienia aplikacji. `commit` Wartość musi być mniejsza lub równa `reserve` wartość.

Określ `reserve` i `commit` wartości dziesiętnych lub języka C notacji szesnastkowej lub ósemkowo. Na przykład wartość 1 MB można określić jako 1048576 w zapisie dziesiętnym, lub 0x100000 w formacie szesnastkowym lub 04000000 w ósemkowej.

## <a name="see-also"></a>Zobacz też

[Opcje EDITBIN](../../build/reference/editbin-options.md)