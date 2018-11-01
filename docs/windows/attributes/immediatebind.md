---
title: immediatebind — (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.immediatebind
helpviewer_keywords:
- immediatebind attribute
ms.assetid: 186d40e6-9166-4d0c-9853-4e7e4d25226f
ms.openlocfilehash: 35e8ea4a761fd3cf36da335dc8519ba71772b4e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50647732"
---
# <a name="immediatebind"></a>immediatebind

Wskazuje, że baza danych zostanie niezwłocznie powiadomiona o wszystkich zmianach właściwości obiektu powiązanych z danymi.

## <a name="syntax"></a>Składnia

```cpp
[immediatebind]
```

## <a name="remarks"></a>Uwagi

**Immediatebind —** atrybut C++ ma taką samą funkcjonalność jak [immediatebind —](/windows/desktop/Midl/immediatebind) atrybutów w MIDL.

## <a name="example"></a>Przykład

Zobacz [możliwej do wiązania](bindable.md) przykład sposobu użycia **immediatebind —**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Metody interfejsu|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)<br/>
[defaultbind](defaultbind.md)<br/>
[displaybind](displaybind.md)<br/>
[requestedit](requestedit.md)