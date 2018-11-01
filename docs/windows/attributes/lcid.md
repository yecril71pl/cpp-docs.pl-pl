---
title: Identyfikator LCID (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.lcid
helpviewer_keywords:
- LCID attribute
ms.assetid: 7f248c69-ee1c-42c3-9411-39cf27c9f43d
ms.openlocfilehash: e431736fcd38b3c08936e65ecf05594142ced4e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655332"
---
# <a name="lcid"></a>lcid

Służy do przekazywania identyfikator ustawień regionalnych do funkcji.

## <a name="syntax"></a>Składnia

```cpp
[lcid]
```

## <a name="remarks"></a>Uwagi

**Lcid** atrybut C++ implementuje funkcje [lcid](/windows/desktop/Midl/lcid) atrybutów w MIDL. Jeśli chcesz wdrożyć ustawienia regionalne dla bloku biblioteki, użyj **lcid =** `lcid` parametr [modułu](module-cpp.md) atrybutu.

## <a name="example"></a>Przykład

```cpp
// cpp_attr_ref_lcid.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLibrary")];
typedef long HRESULT;

[dual, uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA")]
__interface IStatic {
   HRESULT MyFunc([in, lcid] long LocaleID, [out, retval] BSTR * ReturnVal);
};
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Parametr interfejsu|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty parametru](parameter-attributes.md)