---
title: dispinterface (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.dispinterface
helpviewer_keywords:
- dispinterface attribute
ms.assetid: 61c5a4a1-ae92-47e9-8ee4-f847be90172b
ms.openlocfilehash: d0ace76fdbbc1ff930bccb4e6fc203895b4f1637
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677282"
---
# <a name="dispinterface"></a>dispinterface

Przełącza interfejsu w pliku .idl, jako interfejs ekspedycji.

## <a name="syntax"></a>Składnia

```cpp
[dispinterface]
```

## <a name="remarks"></a>Uwagi

Gdy **dispinterface** atrybut C++ poprzedza interfejs, sprawia, że interfejs, który ma być umieszczony wewnątrz bloku biblioteki w pliku .idl wygenerowany.

O ile nie określono klasy bazowej, interfejs ekspedycji, z której pochodzą z `IDispatch`. Należy określić [identyfikator](id.md) dla członków interfejs ekspedycji.

Przykład użycia [dispinterface](/windows/desktop/Midl/dispinterface) w dokumentacji MIDL:

```cpp
dispinterface helloPro
   { interface hello; };
```

nie jest prawidłowa dla **dispinterface** atrybutu.

## <a name="example"></a>Przykład

Zobacz przykład [możliwej do wiązania](bindable.md) przykład sposobu użycia **dispinterface**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**interface**|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|`dual`, `object`, `oleautomation`, `local`, `ms_union`|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty w zależności od zastosowania](attributes-by-usage.md)<br/>
[uuid](uuid-cpp-attributes.md)<br/>
[dual](dual.md)<br/>
[custom](custom-cpp.md)<br/>
[object](object-cpp.md)<br/>
[__interface](../../cpp/interface.md)