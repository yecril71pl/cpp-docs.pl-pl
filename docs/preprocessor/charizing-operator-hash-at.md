---
title: Operator konwersji na znaki (#@)
ms.date: 11/04/2016
f1_keywords:
- '#@'
helpviewer_keywords:
- preprocessor, operators
- charizing operator
- '#@ preprocessor operator'
ms.assetid: dee03314-d27c-4063-965c-64756efbef22
ms.openlocfilehash: 7259487a3289173bc77517c8c616638c370041c4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568349"
---
# <a name="charizing-operator-"></a>Operator konwersji na znaki (#@)
**Microsoft Specific**

Charizing operatora można używać tylko w przypadku argumentów makra. Jeśli `#@` poprzedza parametrów formalnych w definicji makra, rzeczywisty argument jest ujęty w znaki pojedynczego cudzysłowu i traktowany jako znak, po rozwinięciu makra. Na przykład:

```
#define makechar(x)  #@x
```

powoduje, że instrukcja

```
a = makechar(b);
```

Aby rozszerzyć, aby

```
a = 'b';
```

Znak pojedynczego cudzysłowu nie można użyć z operatorem charizing.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Operatory preprocesora](../preprocessor/preprocessor-operators.md)