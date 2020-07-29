---
title: wersja (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.version
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
ms.openlocfilehash: b537f56c39c33abc52897cf53ea2cc0fb24ee458
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213804"
---
# <a name="version-c"></a>version (C++)

Identyfikuje konkretną wersję w wielu wersjach klasy.

## <a name="syntax"></a>Składnia

```cpp
[ version("version") ]
```

### <a name="parameters"></a>Parametry

*Wersja*<br/>
Numer wersji `coclass` . Jeśli nie zostanie określony, 1,0 zostanie umieszczony w pliku. idl.

## <a name="remarks"></a>Uwagi

Atrybut **Version** C++ ma taką samą funkcjonalność jak atrybut MIDL [wersji](/windows/win32/Midl/version) i jest przesyłany do wygenerowanego pliku IDL.

## <a name="example"></a>Przykład

Zobacz przykład [powiązania](bindable.md) dla przykładowego użycia **wersji**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**`class`**, **`struct`**|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|**coclass**|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty kompilatora](compiler-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)
