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
ms.openlocfilehash: 3477f77b811d8bec09b63664a05a4e251214aefa
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213128"
---
# <a name="virtual-c"></a>wirtualne (C++)

**`virtual`** Słowo kluczowe deklaruje funkcję wirtualną lub wirtualną klasę bazową.

## <a name="syntax"></a>Składnia

```
virtual [type-specifiers] member-function-declarator
virtual [access-specifier] base-class-name
```

#### <a name="parameters"></a>Parametry

*Specyfikatory typu*<br/>
Określa zwracany typ wirtualnej funkcji członkowskiej.

*member-Function-deklarator*<br/>
Deklaruje funkcję członkowską.

*specyfikator dostępu*<br/>
Definiuje poziom dostępu do klasy podstawowej, **`public`** **`protected`** lub **`private`** . Może występować przed **`virtual`** słowem kluczowym lub po nim.

*Nazwa klasy podstawowej*<br/>
Identyfikuje poprzednio zadeklarowany typ klasy.

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [funkcje wirtualne](../cpp/virtual-functions.md) .

Zobacz również następujące słowa kluczowe: [Klasa](../cpp/class-cpp.md), [prywatna](../cpp/private-cpp.md), [publiczna](../cpp/public-cpp.md)i [chroniona](../cpp/protected-cpp.md).

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)
