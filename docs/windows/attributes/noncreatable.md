---
title: niemożliwy do utworzeniaC++ (atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.noncreatable
helpviewer_keywords:
- noncreatable attribute
ms.assetid: 4d17937b-0bff-41af-ba57-53e18b7ab5a9
ms.openlocfilehash: e855497cb6f619ecdaa6aedf16a04f045a60faa7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514564"
---
# <a name="noncreatable"></a>noncreatable

Definiuje obiekt, którego nie można utworzyć na podstawie samego siebie.

## <a name="syntax"></a>Składnia

```cpp
[noncreatable]
```

## <a name="remarks"></a>Uwagi

Atrybut niemożliwy do utworzenia ma taką samą funkcjonalność jak atrybut [](/windows/win32/Midl/noncreatable) MIDL, którego nie można uzyskać, i jest automatycznie przenoszona do wygenerowanego. C++ Plik IDL przez kompilator.

Gdy ten atrybut jest używany w projekcie, który korzysta z ATL, zachowanie atrybutu zostanie zmienione. Oprócz powyższych zachowań atrybut również wprowadza makro [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) . To makro wskazuje na ATL, że nie można utworzyć obiektu zewnętrznie.

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

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Klasa**, **Struktura**|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|**coclass**|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)
