---
title: switch_type — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.switch_type
dev_langs:
- C++
helpviewer_keywords:
- switch_type attribute
ms.assetid: e24544dc-b3bc-48ae-b249-f967db49271e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: faa2a3be7260eecb16599db967336bcb7b774c99
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200129"
---
# <a name="switchtype"></a>switch_type

Określa typ zmiennej używanej jako discriminant Unii.

## <a name="syntax"></a>Składnia

```cpp
[switch_type(
type
}]
```

### <a name="parameters"></a>Parametry

*Typ*  
Typ przełącznika może być typu Liczba całkowita, znaku, wartość logiczna lub wyliczenia.

## <a name="remarks"></a>Uwagi

**Switch_type —** atrybut C++ ma taką samą funkcjonalność jak [switch_type —](/windows/desktop/Midl/switch-type) atrybutów w MIDL.

Atrybuty C++ nie obsługują [hermetyzowane unie](/windows/desktop/Midl/encapsulated-unions). [Unie nonencapsulated](/windows/desktop/Midl/nonencapsulated-unions) są obsługiwane tylko w następującej postaci:

```cpp
// cpp_attr_ref_switch_type.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLibrary")];
[ export ]
struct SizedValue2 {
   [switch_type("char"), switch_is(kind)] union {
      [case(1), string]
         wchar_t* wval;
      [default, string]
         char* val;
   };
   char kind;
};
```

## <a name="example"></a>Przykład

Zobacz [przypadek](../windows/case-cpp.md) przykład użycie próbki **switch_type —**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Element TypeDef**|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](../windows/idl-attributes.md)  
[Atrybuty Typedef, Enum, Union oraz Struct](../windows/typedef-enum-union-and-struct-attributes.md)  
[export](../windows/export.md)  