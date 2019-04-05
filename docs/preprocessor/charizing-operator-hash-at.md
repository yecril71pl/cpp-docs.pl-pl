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
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59034338"
---
# <a name="charizing-operator-"></a>Operator konwersji na znaki (#@)
**Specyficzne dla firmy Microsoft**

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

**KONIEC Specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz także

[Operatory preprocesora](../preprocessor/preprocessor-operators.md)