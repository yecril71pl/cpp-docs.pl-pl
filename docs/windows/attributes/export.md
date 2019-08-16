---
title: Export (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.export
helpviewer_keywords:
- export attribute
ms.assetid: 70b3e848-fad6-4e09-8c72-be60ca72a4df
ms.openlocfilehash: 771bfdfe4eab2acf31e97a606795066e8938a8a1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501603"
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

Jeśli eksportujesz nienazwane **Wyliczenie** lub **strukturę**, otrzymujesz nazwę rozpoczynającą się od **__unnamed**<em>x</em>, gdzie *x* jest numerem sekwencyjnym.

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
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty kompilatora](compiler-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)