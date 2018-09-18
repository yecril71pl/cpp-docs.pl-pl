---
title: Ocena tokenów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- tokens, evaluating
ms.assetid: 28870b62-dff6-4644-8b75-d58f340b48d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5d5c79ac043b2131df7a876f2de63922c45c9ead
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035282"
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

## <a name="see-also"></a>Zobacz też

[Tokeny języka C](../c-language/c-tokens.md)