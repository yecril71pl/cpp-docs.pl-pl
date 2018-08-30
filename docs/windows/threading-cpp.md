---
title: wątkowość (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.threading
dev_langs:
- C++
helpviewer_keywords:
- threading attribute
ms.assetid: 9b558cd6-fbf0-4602-aed5-31c068550ce3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 19f49951cad65d3dbf15c406af9ac78a28408d4b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221817"
---
# <a name="threading-c"></a>threading (C++)

Określa model wątkowości dla obiektu COM.

## <a name="syntax"></a>Składnia

```cpp
[ threading(
   model=enumeration
) ]
```

### <a name="parameters"></a>Parametry

*model* (opcjonalnie)  
Jeden z następujących Modele wątkowości:

- `apartment` (wątkowości typu apartment)

- `neutral` (Składników .NET framework bez interfejsu użytkownika)

- `single` (wątki proste)

- `free` (bezpłatnie, wątki)

- `both` (apartamentu i wolnych wątków)

Wartość domyślna to `apartment`.

## <a name="remarks"></a>Uwagi

**Wątkowości** atrybut C++ nie ma pliku .idl wygenerowane, ale będą stosowane w implementacji obiektu COM.

W projektach ATL Jeśli [coclass](../windows/coclass.md) również jest obecny, atrybut modelu wątku określonego przez *modelu* jest przekazywany jako parametr szablonu [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) klasy , wstawione przez `coclass` atrybutu.

**Wątkowości** atrybut chroni także dostęp do [event_source](../windows/event-source.md).

## <a name="example"></a>Przykład

Zobacz [licencjonowane](../windows/licensed.md) przykład użycie próbki **wątkowości**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Klasa**, **— struktura**|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|**coclass**|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).

## <a name="see-also"></a>Zobacz też

[Atrybuty COM](../windows/com-attributes.md)  
[Atrybuty Typedef, Enum, Union oraz Struct](../windows/typedef-enum-union-and-struct-attributes.md)  
[Atrybuty klasy](../windows/class-attributes.md)  
[Obsługa wielowątkowości w przypadku starszego kodu (Visual C++)](../parallel/multithreading-support-for-older-code-visual-cpp.md)  
[Neutralne Apartamentach](/windows/desktop/cossdk/neutral-apartments)  