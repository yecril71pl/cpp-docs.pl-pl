---
title: Ocena tokenów
ms.date: 11/04/2016
helpviewer_keywords:
- tokens, evaluating
ms.assetid: 28870b62-dff6-4644-8b75-d58f340b48d2
ms.openlocfilehash: 15775ca9a7ada46aaf4e53ae952cd67e95bbf8d3
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152550"
---
# <a name="evaluation-of-tokens"></a>Ocena tokenów

Gdy kompilator interpretuje słowa kluczowe tokenów, zawiera maksymalną liczbę znaków jak to możliwe w pojedynczy token przed przejściem do następnego tokenu. Ze względu na to zachowanie kompilator nie może zinterpretować tokenów poprawnie, jeśli ich nie są poprawnie rozdzielone biały znak. Należy wziąć pod uwagę następujące wyrażenie:

```
i+++j
```

W tym przykładzie, kompilator najpierw sprawia, że najdłuższy możliwe — operator (`++`) z trzech znak plus, a następnie przetwarza pozostałe znak plus jako operator dodawania (`+`). W związku z tym, wyrażenie jest interpretowany jako `(i++) + (j)`, a nie `(i) + (++j)`. W tym i podobnych przypadków używają biały znak i nawiasy, aby uniknąć niejednoznaczności i zapewnienia prawidłowego wyrażenia.

**Microsoft Specific**

Kompilator języka C traktuje znaku CTRL + Z jako wskaźnik końca pliku. Ignoruje wszelki tekst po CTRL + Z.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Tokeny języka C](../c-language/c-tokens.md)
