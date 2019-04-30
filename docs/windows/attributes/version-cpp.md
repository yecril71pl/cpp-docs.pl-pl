---
title: Wersja (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.version
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
ms.openlocfilehash: fe1df9e12b9adbf9ce55978fd3479f7e740ddc96
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407162"
---
# <a name="version-c"></a>version (C++)

Identyfikuje określoną wersję spośród wielu wersji klasy.

## <a name="syntax"></a>Składnia

```cpp
[ version("version") ]
```

### <a name="parameters"></a>Parametry

*version*<br/>
Numer wersji `coclass`. Jeśli nie zostanie określony, 1.0 zostanie umieszczona w pliku .idl.

## <a name="remarks"></a>Uwagi

**Wersji** atrybut C++ ma taką samą funkcjonalność jak [wersji](/windows/desktop/Midl/version) atrybutów w MIDL i jest przekazywana do pliku .idl wygenerowany.

## <a name="example"></a>Przykład

Zobacz [możliwej do wiązania](bindable.md) przykład użycie próbki **wersji**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Klasa**, **— struktura**|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|**coclass**|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty kompilatora](compiler-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)