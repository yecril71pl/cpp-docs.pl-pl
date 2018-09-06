---
title: Operator konwersji na znaki (#@) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#@'
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, operators
- charizing operator
- '#@ preprocessor operator'
ms.assetid: dee03314-d27c-4063-965c-64756efbef22
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d86c49c8d7d0cda91ba2415167cc79c810a96b3d
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43895308"
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