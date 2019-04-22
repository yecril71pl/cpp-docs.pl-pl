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
ms.openlocfilehash: c9acc9b9872e096cd441b950632c341e975fecb8
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59034338"
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

## <a name="see-also"></a>Zobacz także

[Operatory preprocesora](../preprocessor/preprocessor-operators.md)