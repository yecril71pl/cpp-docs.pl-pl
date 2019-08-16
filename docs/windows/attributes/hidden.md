---
title: ukryty (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.hidden
helpviewer_keywords:
- hidden attribute
ms.assetid: 199c96dd-fc07-46c7-af93-92020aebebe7
ms.openlocfilehash: 75b03877b1204d6e1c4770f5ba9c8c88338b3394
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501448"
---
# <a name="hidden"></a>hidden

Wskazuje, że element istnieje, ale nie powinien być wyświetlany w przeglądarce zorientowanej na użytkownika.

## <a name="syntax"></a>Składnia

```cpp
[hidden]
```

## <a name="remarks"></a>Uwagi

Atrybut **Hidden** C++ ma takie same funkcje jak [ukryty](/windows/win32/Midl/hidden) atrybut MIDL.

## <a name="example"></a>Przykład

Zobacz przykład dla [powiązania](bindable.md) z przykładem, jak używać **ukrytego**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**interfejs**, **Klasa**, **Struktura**, metoda, właściwość|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|**Klasa coclass** (w przypadku zastosowania do **klasy** lub **struktury**)|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)