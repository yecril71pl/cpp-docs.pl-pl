---
title: wirtualne (C++)
ms.date: 11/04/2016
f1_keywords:
- virtual_cpp
- virtual
helpviewer_keywords:
- virtual base classes [C++], declaring
- base classes [C++], virtual
- virtual functions [C++], declaring
- virtual keyword [C++]
ms.assetid: c2eb987d-6cf3-43b6-aa0c-29a6f561b1ae
ms.openlocfilehash: f68bd2e500ebe16c43ef6c3d7a5aede26421b27d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393912"
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

*member-function-declarator*<br/>
Deklaruje funkcję członkowską.

*access-specifier*<br/>
Określa poziom dostępu do klasy bazowej, **publicznych**, **chronione** lub **prywatnej**. Może znajdować się przed lub po **wirtualnego** — słowo kluczowe.

*base-class-name*<br/>
Określa typ klasy zadeklarowanej wcześniej.

## <a name="remarks"></a>Uwagi

Zobacz [funkcji wirtualnych](../cpp/virtual-functions.md) Aby uzyskać więcej informacji.

Zobacz też następujące słowa kluczowe: [klasy](../cpp/class-cpp.md), [prywatnej](../cpp/private-cpp.md), [publicznych](../cpp/public-cpp.md), i [chronione](../cpp/protected-cpp.md).

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)