---
title: Synchronizuj (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.synchronize
helpviewer_keywords:
- synchronize attribute
ms.assetid: 15fc8544-955d-4765-b3d5-0f619c8b3f40
ms.openlocfilehash: a0f4702de4cfde8586cc573f9ff5a6195984d207
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214516"
---
# <a name="synchronize"></a>synchronize

Synchronizuje dostęp do metody docelowej.

## <a name="syntax"></a>Składnia

```cpp
[synchronize]
```

## <a name="remarks"></a>Uwagi

Atrybut **Synchronize** C++ implementuje obsługę synchronizowania metody docelowej obiektu. Synchronizacja umożliwia wielu obiektom użycie wspólnego zasobu (takiego jak metoda klasy) poprzez kontrolowanie dostępu do metody docelowej.

Kod wstawiony przez ten atrybut wywołuje właściwą metodę `Lock` (określoną przez model wątkowości) na początku metody docelowej. Gdy metoda zostanie zakończona, `Unlock` jest wywoływana automatycznie. Aby uzyskać więcej informacji na temat tych funkcji, zobacz [CComAutoThreadModule:: Lock](../../atl/reference/ccomautothreadmodule-class.md#lock)

Ten atrybut wymaga, aby atrybut [coclass](coclass.md), [ProgID](progid.md)lub [vi_progid](vi-progid.md) (lub inny atrybut, który implikuje jeden z tych) został również zastosowany do tego samego elementu. W przypadku użycia dowolnego pojedynczego atrybutu zostaną automatycznie zastosowane pozostałe dwa. Na przykład jeśli `progid` jest stosowany, `vi_progid` i `coclass` są również stosowane.

## <a name="example"></a>Przykład

Poniższy kod umożliwia synchronizację metody `UpdateBalance` obiektu `CMyClass`.

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

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Metoda klasy, Metoda|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Co najmniej jeden z następujących elementów: `coclass`, `progid`lub `vi_progid`.|
|**Nieprawidłowe atrybuty**|None|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty COM](com-attributes.md)
