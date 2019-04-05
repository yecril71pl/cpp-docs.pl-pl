---
title: Eksportuj (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.export
helpviewer_keywords:
- export attribute
ms.assetid: 70b3e848-fad6-4e09-8c72-be60ca72a4df
ms.openlocfilehash: 5ffa4283b8a2b265809d06b72be96e217cf8bf9f
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023610"
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
|**Informacje zawarte w tym artykule dotyczą**|**Unia**, **typedef**, **wyliczenia**, **struktury**, lub **interfejsu**|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty kompilatora](compiler-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)