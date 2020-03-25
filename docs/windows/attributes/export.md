---
title: Export (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.export
helpviewer_keywords:
- export attribute
ms.assetid: 70b3e848-fad6-4e09-8c72-be60ca72a4df
ms.openlocfilehash: 6264db037069f5fc6b858bdd466ce6c68b814a84
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167047"
---
# <a name="export"></a>export

Powoduje, że struktura danych zostanie umieszczona w pliku IDL.

## <a name="syntax"></a>Składnia

```cpp
[export]
```

## <a name="remarks"></a>Uwagi

Atrybut **Export** C++ powoduje, że struktura danych zostanie umieszczona w pliku. idl, a następnie dostępna w bibliotece typów w formacie zgodnym z binarnym, dzięki czemu można go używać z dowolnym językiem.

Nie można zastosować atrybutu **Export** do klasy, nawet jeśli klasa ma tylko publiczne elementy członkowskie (odpowiednik **struktury**).

Jeśli eksportujesz nienazwane **Wyliczenie** lub **strukturę**, otrzymujesz nazwę zaczynającą się od **__unnamed**<em>x</em>, gdzie *x* jest numerem sekwencyjnym.

Elementy typedef są prawidłowe dla eksportu są typami podstawowymi, strukturami, związkami, wyliczeniami lub identyfikatorami typów.  Aby uzyskać więcej informacji, zobacz [element typedef](/windows/win32/Midl/typedef) .

## <a name="example"></a>Przykład

Poniższy kod pokazuje, jak używać atrybutu **Export** :

```cpp
// cpp_attr_ref_export.cpp
// compile with: /LD
[module(name="MyLibrary")];

[export]
struct MyStruct {
   int i;
};
```

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Union**, **typedef**, **enum**, **struct**lub **Interface**|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|None|
|**Nieprawidłowe atrybuty**|None|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty kompilatora](compiler-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)
