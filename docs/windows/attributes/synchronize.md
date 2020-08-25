---
title: Synchronizuj (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.synchronize
helpviewer_keywords:
- synchronize attribute
ms.assetid: 15fc8544-955d-4765-b3d5-0f619c8b3f40
ms.openlocfilehash: a7edbaa4e572af18bec9b3b6bef54594d6511390
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831674"
---
# <a name="synchronize"></a>synchronize

Synchronizuje dostęp do metody docelowej.

## <a name="syntax"></a>Składnia

```cpp
[synchronize]
```

## <a name="remarks"></a>Uwagi

Atrybut **Synchronize** C++ implementuje obsługę synchronizowania metody docelowej obiektu. Synchronizacja umożliwia wielu obiektom użycie wspólnego zasobu (takiego jak metoda klasy) poprzez kontrolowanie dostępu do metody docelowej.

Kod wstawiony przez ten atrybut wywołuje właściwą `Lock` metodę (określoną przez model wątkowości) na początku metody docelowej. Gdy metoda zostanie zakończona, `Unlock` jest automatycznie wywoływana. Aby uzyskać więcej informacji na temat tych funkcji, zobacz [CComAutoThreadModule:: Lock](../../atl/reference/ccomautothreadmodule-class.md#lock)

Ten atrybut wymaga, aby atrybut [coclass](coclass.md), [ProgID](progid.md)lub [vi_progid](vi-progid.md) (lub inny atrybut, który implikuje jeden z tych) został również zastosowany do tego samego elementu. W przypadku użycia dowolnego pojedynczego atrybutu zostaną automatycznie zastosowane pozostałe dwa. Na przykład, jeśli `progid` jest stosowany, `vi_progid` i `coclass` są również stosowane.

## <a name="example"></a>Przykład

Poniższy kod umożliwia synchronizację `UpdateBalance` metody `CMyClass` obiektu.

```cpp
// cpp_attr_ref_synchronize.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module(name="SYNC")];

[coclass,
threading(both),
vi_progid("MyProject.MyClass"),
progid("MyProject.MyClass.1"),
uuid("7a7baa0d-59b8-4576-b754-79d07e1d1cc3")
]
class CMyClass {
   float m_nBalance;

   [synchronize]
   void UpdateBalance(float nAdjust) {
      m_nBalance += nAdjust;
   }
};
```

## <a name="requirements"></a>Wymagania

| Kontekst atrybutu | Wartość |
|-|-|
|**Dotyczy**|Metoda klasy, Metoda|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Co najmniej jeden z następujących elementów: `coclass` , `progid` , lub `vi_progid` .|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty COM](com-attributes.md)
