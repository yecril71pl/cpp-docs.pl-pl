---
title: wirtualne (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- virtual_cpp
- virtual
dev_langs:
- C++
helpviewer_keywords:
- virtual base classes [C++], declaring
- base classes [C++], virtual
- virtual functions [C++], declaring
- virtual keyword [C++]
ms.assetid: c2eb987d-6cf3-43b6-aa0c-29a6f561b1ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2471dac12db574aa045142a654effafadbabd732
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092275"
---
# <a name="virtual-c"></a>wirtualne (C++)

**Wirtualnego** — słowo kluczowe deklaruje funkcję wirtualną lub wirtualnej klasy bazowej.

## <a name="syntax"></a>Składnia

```
virtual [type-specifiers] member-function-declarator
virtual [access-specifier] base-class-name
```

#### <a name="parameters"></a>Parametry

*Specyfikatory typów*<br/>
Określa typ zwracany funkcja wirtualna elementu członkowskiego.

*deklaratora w przypadku funkcji składowej*<br/>
Deklaruje funkcję członkowską.

*Specyfikator dostępu*<br/>
Określa poziom dostępu do klasy bazowej, **publicznych**, **chronione** lub **prywatnej**. Może znajdować się przed lub po **wirtualnego** — słowo kluczowe.

*Base-class-name*<br/>
Określa typ klasy zadeklarowanej wcześniej.

## <a name="remarks"></a>Uwagi

Zobacz [funkcji wirtualnych](../cpp/virtual-functions.md) Aby uzyskać więcej informacji.

Zobacz też następujące słowa kluczowe: [klasy](../cpp/class-cpp.md), [prywatnej](../cpp/private-cpp.md), [publicznych](../cpp/public-cpp.md), i [chronione](../cpp/protected-cpp.md).

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)