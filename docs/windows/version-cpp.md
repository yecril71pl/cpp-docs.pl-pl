---
title: Wersja (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.version
dev_langs:
- C++
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 87186ee70b5863f51a7cd91f8695052f361bd11c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43222535"
---
# <a name="version-c"></a>version (C++)

Identyfikuje określoną wersję spośród wielu wersji klasy.

## <a name="syntax"></a>Składnia

```cpp
[ version(
   "version"
) ]
```

### <a name="parameters"></a>Parametry

*Wersja*  
Numer wersji `coclass`. Jeśli nie zostanie określony, 1.0 zostanie umieszczona w pliku .idl.

## <a name="remarks"></a>Uwagi

**Wersji** atrybut C++ ma taką samą funkcjonalność jak [wersji](/windows/desktop/Midl/version) atrybutów w MIDL i jest przekazywana do pliku .idl wygenerowany.

## <a name="example"></a>Przykład

Zobacz [możliwej do wiązania](../windows/bindable.md) przykład użycie próbki **wersji**.

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

[Atrybuty kompilatora](../windows/compiler-attributes.md)  
[Atrybuty klasy](../windows/class-attributes.md)  