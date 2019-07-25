---
title: '&lt;string_view&gt;'
ms.date: 04/18/2019
helpviewer_keywords:
- string_view header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
ms.openlocfilehash: 47924c3d6bd1a2f45cdbac648f4f563c57ce8939
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459118"
---
# <a name="ltstringviewgt"></a>&lt;string_view&gt;

Definiuje szablon `basic_string_view` klasy i powiązane typy oraz operatory. (Wymaga opcji kompilatora [std: c++ 17](../build/reference/std-specify-language-standard-version.md) lub nowszej).

## <a name="syntax"></a>Składnia

```cpp
#include <string_view>
```

## <a name="remarks"></a>Uwagi

Rodzina string_viewych specjalizacji szablonów zapewnia wydajny sposób przekazywania dojścia do odczytu, bezpiecznego wyjątku, niebędącego właścicielem, do danych znakowych dowolnego obiektu podobnego do ciągu z pierwszym elementem sekwencji w pozycji zero. Parametr funkcji typu `string_view` (, który jest elementem TypeDef dla `basic_string_view<char>`) może przyjmować argumenty takie jak `std::string`, **char\*** lub wszelkie inne klasy podobne do ciągów o wąskich znakach, dla których niejawna konwersja na `string_view`jest zdefiniowany. Analogicznie, parametr `wstring_view`lub `u32string_view` może `u16string_view` akceptować dowolny typ ciągu, dla którego zdefiniowano niejawną konwersję. Aby uzyskać więcej informacji, zobacz [Klasa basic_string_view](../standard-library/basic-string-view-class.md).

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[string_view](../standard-library/string-view-typedefs.md#string_view)|Specjalizacja szablonu `basic_string_view` klasy z elementami typu **char**.|
|[wstring_view](../standard-library/string-view-typedefs.md#wstring_view)|Specjalizacja szablonu `basic_string_view` klasy z elementami typu **wchar_t**.|
|[u16string_view](../standard-library/string-view-typedefs.md#u16string_view)|Specjalizacja szablonu `basic_string_view` klasy z elementami typu `char16_t`.|
|[u32string_view](../standard-library/string-view-typedefs.md#u32string_view)|Specjalizacja szablonu `basic_string_view` klasy z elementami typu `char32_t`.|

### <a name="operators"></a>Operatory

`string_view` Operatory > \<string_view mogą porównywać obiekty z obiektami dowolnego typu ciągu z możliwością konwersji.

|Operator|Opis|
|-|-|
|[operator!=](../standard-library/string-view-operators.md#op_neq)|Testuje, czy obiekt po lewej stronie operatora nie jest równy obiektowi po prawej stronie.|
|[operator==](../standard-library/string-view-operators.md#op_eq_eq)|Testuje, czy obiekt po lewej stronie operatora jest równy obiektowi po prawej stronie.|
|[< operatora](../standard-library/string-view-operators.md#op_lt)|Testuje, czy obiekt po lewej stronie operatora jest mniejszy od obiektu po prawej stronie.|
|[< operatora =](../standard-library/string-view-operators.md#op_lt_eq)|Testuje, czy obiekt po lewej stronie operatora jest mniejszy od lub równy obiektowi po prawej stronie.|
|[< operatora\<](../standard-library/string-view-operators.md#op_lt_lt)|Funkcja szablonu, która wstawia `string_view` do strumienia wyjściowego.|
|[operator>](../standard-library/string-view-operators.md#op_gt)|Testuje, czy obiekt po lewej stronie operatora jest większy niż obiekt po prawej stronie.|
|[operator>=](../standard-library/string-view-operators.md#op_gt_eq)|Testuje, czy obiekt po lewej stronie operatora jest większy niż lub równy obiektowi po prawej stronie.|

### <a name="literals"></a>Literały

|Operator|Opis|
|-|-|
|[OHR](../standard-library/string-view-operators.md#op_sv)|`string_view`Tworzy `wstring_view` ,,`u32string_view` lub w zależności od typu literału ciągu, doktóregojestdołączany.`u16string_view`|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[basic_string_view, klasa](../standard-library/basic-string-view-class.md)|Szablon klasy, który udostępnia widok tylko do odczytu w sekwencji dowolnych obiektów podobnej do znaku.|
|[skrótu](string-view-hash.md)|Obiekt funkcyjny, który generuje wartość skrótu dla string_view.|

## <a name="requirements"></a>Wymagania

- **Nagłówek:** \<string_view >

- **Przestrzeń nazw:** std

- **Opcja kompilatora:** std: c++ 17 (lub nowsza)

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
