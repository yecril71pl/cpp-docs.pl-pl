---
title: Eksportuj (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.export
helpviewer_keywords:
- export attribute
ms.assetid: 70b3e848-fad6-4e09-8c72-be60ca72a4df
ms.openlocfilehash: 951c0ef2f0da0fa897c299aa6b547d5c0788b285
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661594"
---
# <a name="export"></a>export

Powoduje to struktura danych, należy umieścić w pliku .idl.

## <a name="syntax"></a>Składnia

```cpp
[export]
```

## <a name="remarks"></a>Uwagi

**Wyeksportować** C++ atrybutu powoduje, że struktury danych, można umieścić w pliku .idl i następnie być dostępne w bibliotece typów w formacie zgodnym z pliku binarnego, który sprawia, że dostępne w dowolnym języku.

Nie można zastosować **wyeksportować** atrybutów do klasy, nawet wtedy, gdy klasa ma tylko publiczne elementy członkowskie (odpowiednik **struktury**).

Jeśli eksportujesz nienazwane **wyliczenia** lub **struktury**, otrzymuje nazwę, która rozpoczyna się od **__unnamed**<em>x</em>, gdzie *x* jest to numer kolejny.

Definicje typów prawidłowe eksportu są typy podstawowe, struktury, złożenia, wyliczenia lub wpisz identyfikatory.  Zobacz [typedef](/windows/desktop/Midl/typedef) Aby uzyskać więcej informacji.

## <a name="example"></a>Przykład

Poniższy kod przedstawia sposób użycia **wyeksportować** atrybutu:

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
|**Dotyczy**|**Unia**, **typedef**, **wyliczenia**, **struktury**, lub **interfejsu**|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty kompilatora](compiler-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)