---
title: retval (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.retval
helpviewer_keywords:
- retval attribute
ms.assetid: bfa16f08-157d-4eea-afde-1232c54b8501
ms.openlocfilehash: 5aded4588614eb4171e31a588f125ea8aa8de7ee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166344"
---
# <a name="retval"></a>retval

Określa parametr, który odbiera wartość zwracaną przez element członkowski.

## <a name="syntax"></a>Składnia

```cpp
[retval]
```

## <a name="remarks"></a>Uwagi

Atrybut **retval** C++ ma takie same funkcje [jak MIDL.](/windows/win32/Midl/retval)

element **retval** musi znajdować się na ostatnim argumencie w deklaracji funkcji.

## <a name="example"></a>Przykład

Zapoznaj się z przykładem [powiązania](bindable.md) dla przykładowego użycia programu **retval**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Parametr interfejsu, metoda interfejsu|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|**out**|
|**Nieprawidłowe atrybuty**|**in**|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty parametru](parameter-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)
