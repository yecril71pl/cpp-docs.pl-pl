---
title: helpstringdll — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpstringdll
dev_langs:
- C++
helpviewer_keywords:
- helpstringdll attribute [C++]
ms.assetid: 121271fa-f061-492b-b87f-bbfcf4b02e7b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bc10f86a8fa646a1072de8b7c5e30121d98750cf
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43219955"
---
# <a name="helpstringdll"></a>helpstringdll

Określa nazwę biblioteki DLL, aby wykonać wyszukiwanie ciągu dokumentu (lokalizacja).

## <a name="syntax"></a>Składnia

```cpp
[ helpstringdll(
   "string"
) ]
```

### <a name="parameters"></a>Parametry

*string*  
Biblioteki DLL, użyj, aby wykonać wyszukiwanie ciągu dokumentu.

## <a name="remarks"></a>Uwagi

**Helpstringdll —** atrybut C++ ma taką samą funkcjonalność jak [helpstringdll —](/windows/desktop/Midl/helpstringdll) atrybutów w MIDL.

## <a name="example"></a>Przykład

```cpp
// cpp_attr_ref_helpstringdll.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib", helpstringdll="xx.dll")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI
{
   HRESULT xxx();
};
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Klasa**, **interfejsu**, interfejs — metoda|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](../windows/idl-attributes.md)  
[Atrybuty interfejsu](../windows/interface-attributes.md)  
[Atrybuty klasy](../windows/class-attributes.md)  
[Atrybuty metody](../windows/method-attributes.md)  