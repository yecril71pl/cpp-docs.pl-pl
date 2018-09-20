---
title: appobject — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.appobject
dev_langs:
- C++
helpviewer_keywords:
- appobject attribute
ms.assetid: 8ce30b73-e945-403e-a755-6bc78078a695
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fafdb99296e19318f183b6c0893d9b4e91f0cd7b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422639"
---
# <a name="appobject"></a>appobject

Identyfikuje coclass jako obiekt aplikacji, który jest skojarzony z aplikacją pełną .exe i wskazuje, że funkcje i właściwości z koklas, globalnie dostępną w tym [biblioteki typów](../mfc/automation-clients-using-type-libraries.md).

## <a name="syntax"></a>Składnia

```cpp
[appobject]
```

## <a name="remarks"></a>Uwagi

**Appobject —** atrybut C++ ma taką samą funkcjonalność jak [appobject —](/windows/desktop/Midl/appobject) atrybutów w MIDL.

## <a name="example"></a>Przykład

Poniższy kod przedstawia definicję klasy prosty, poprzedzony przez blok atrybutu, który zawiera **appobject —**:

```cpp
// cpp_attr_ref_appobject.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLib", uuid="f1ce17f0-a5df-4d26-95f6-0a122197ac5b")];

[object, uuid="905de6db-7a12-45ab-9f8b-b39f5112f010"]
__interface ICustom {};

[coclass, appobject,uuid="00395340-745f-4b69-bd58-e2921452b9fc"]
class A : public ICustom {
   int i;
};
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Klasa**, **— struktura**|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|`coclass`|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](../windows/idl-attributes.md)<br/>
[Atrybuty klasy](../windows/class-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](../windows/typedef-enum-union-and-struct-attributes.md)  