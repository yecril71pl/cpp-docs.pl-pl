---
title: niemożliwy do utworzenia (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.noncreatable
helpviewer_keywords:
- noncreatable attribute
ms.assetid: 4d17937b-0bff-41af-ba57-53e18b7ab5a9
ms.openlocfilehash: b645d6d6cbcaeff346437d6457360ecdef8d3190
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840560"
---
# <a name="noncreatable"></a>noncreatable

Definiuje obiekt, którego nie można utworzyć na podstawie samego siebie.

## <a name="syntax"></a>Składnia

```cpp
[noncreatable]
```

## <a name="remarks"></a>Uwagi

Atrybut **języka C++ niemożliwy do utworzenia** ma taką samą funkcjonalność jak [atrybut MIDL,](/windows/win32/Midl/noncreatable) którego nie można uzyskać, i jest automatycznie przenoszona do wygenerowanego. Plik IDL przez kompilator.

Gdy ten atrybut jest używany w projekcie, który korzysta z ATL, zachowanie atrybutu zostanie zmienione. Oprócz powyższych zachowań atrybut wprowadza również makro [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) . To makro wskazuje na ATL, że nie można utworzyć obiektu zewnętrznie.

## <a name="example"></a>Przykład

```cpp
// cpp_attr_ref_noncreatable.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[object, uuid("11111111-1111-1111-1111-111111111111")]
__interface A
{
};

[coclass, uuid("11111111-1111-1111-1111-111111111112"), noncreatable]
class CMyClass : public A
{
   HRESULT xx();
};
```

## <a name="requirements"></a>Wymagania

| Kontekst atrybutu | Wartość |
|-|-|
|**Dotyczy**|**`class`**, **`struct`**|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|**coclass**|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)
