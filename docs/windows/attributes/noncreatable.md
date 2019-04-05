---
title: noncreatable — (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.noncreatable
helpviewer_keywords:
- noncreatable attribute
ms.assetid: 4d17937b-0bff-41af-ba57-53e18b7ab5a9
ms.openlocfilehash: a10d93650c0ae564019a09b34c3a604d12327998
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59039994"
---
# <a name="noncreatable"></a>noncreatable

Definiuje obiekt, który nie może być utworzone samodzielnie.

## <a name="syntax"></a>Składnia

```cpp
[noncreatable]
```

## <a name="remarks"></a>Uwagi

**Noncreatable —** atrybut C++ ma taką samą funkcjonalność jak [noncreatable —](/windows/desktop/Midl/noncreatable) atrybutów w MIDL i jest automatycznie przekazywana do wygenerowany. Plik IDL przez kompilator.

Jeśli ten atrybut jest używany w projekcie, który korzysta z biblioteki ATL, zachowanie zmiany atrybutów. Oprócz powyższych zachowanie wprowadza również atrybut [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) makra. To makro wskazuje ATL, że obiekt nie może zostać utworzona zewnętrznie.

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
|**Informacje zawarte w tym artykule dotyczą**|**Klasa**, **— struktura**|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|**coclass**|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)
