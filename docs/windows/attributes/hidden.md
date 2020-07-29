---
title: ukryty (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.hidden
helpviewer_keywords:
- hidden attribute
ms.assetid: 199c96dd-fc07-46c7-af93-92020aebebe7
ms.openlocfilehash: e0e3c5cb0355f3bedd8ecee57b034f0d9dde87df
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224438"
---
# <a name="hidden"></a>hidden

Wskazuje, że element istnieje, ale nie powinien być wyświetlany w przeglądarce zorientowanej na użytkownika.

## <a name="syntax"></a>Składnia

```cpp
[hidden]
```

## <a name="remarks"></a>Uwagi

**Ukryty** atrybut C++ ma taką samą funkcjonalność jak [ukryty](/windows/win32/Midl/hidden) atrybut MIDL.

## <a name="example"></a>Przykład

Zobacz przykład dla [powiązania](bindable.md) z przykładem, jak używać **ukrytego**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**interfejs**, **`class`** , **`struct`** , metoda, właściwość|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|**coclass** (w przypadku zastosowania do **`class`** lub **`struct`** )|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)
