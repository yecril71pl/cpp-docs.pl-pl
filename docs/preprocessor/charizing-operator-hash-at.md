---
title: Operator konwersji na znaki (#@)
ms.date: 08/29/2019
f1_keywords:
- '#@'
helpviewer_keywords:
- preprocessor, operators
- charizing operator
- '#@ preprocessor operator'
ms.assetid: dee03314-d27c-4063-965c-64756efbef22
ms.openlocfilehash: cb2a4e07287edf5ed2d0850ec7d870c8ef307879
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218531"
---
# <a name="charizing-operator-"></a>Operator konwersji na znaki (#@)

**Microsoft Specific**

Operatora konwersji na znaki można używać tylko z argumentami makr. Jeśli `#@` poprzedza parametr formalny w definicji makra, rzeczywisty argument jest ujęty w znaki pojedynczego cudzysłowu i traktowany jako znak, gdy makro jest rozwinięte. Na przykład:

```cpp
#define makechar(x)  #@x
```

powoduje, że instrukcja

```cpp
a = makechar(b);
```

Aby można było rozwijać

```cpp
a = 'b';
```

Znak pojedynczego cudzysłowu (`'`) nie może być używany z operatorem konwersji na znaki.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Operatory preprocesora](../preprocessor/preprocessor-operators.md)
