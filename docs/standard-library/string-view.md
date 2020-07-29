---
title: '&lt;string_view&gt;'
ms.date: 04/18/2019
helpviewer_keywords:
- string_view header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
ms.openlocfilehash: 13b6f5c63b9426fc4c31527f0d1ae8291d07807f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222215"
---
# <a name="ltstring_viewgt"></a>&lt;string_view&gt;

Definiuje szablon klasy `basic_string_view` i powiązane typy oraz operatory. (Wymaga opcji kompilatora [std: c++ 17](../build/reference/std-specify-language-standard-version.md) lub nowszej).

## <a name="syntax"></a>Składnia

```cpp
#include <string_view>
```

## <a name="remarks"></a>Uwagi

Rodzina string_view specjalizacji szablonów zapewnia wydajny sposób przekazywania dojścia do odczytu, bezpiecznego wyjątku, niebędącego właścicielem, do danych znakowych dowolnego obiektu, takiego jak ciąg, z pierwszym elementem sekwencji w pozycji zero. Parametr funkcji typu `string_view` (który jest elementem TypeDef dla `basic_string_view<char>` ) może przyjmować argumenty takie jak `std::string` , **char \* **lub wszelkie inne klasy podobne do ciągów o wąskich znakach, dla których zdefiniowano niejawną konwersję `string_view` . Analogicznie, parametr `wstring_view` `u16string_view` lub `u32string_view` może akceptować dowolny typ ciągu, dla którego zdefiniowano niejawną konwersję. Aby uzyskać więcej informacji, zobacz [Basic_string_view Class](../standard-library/basic-string-view-class.md).

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[string_view](../standard-library/string-view-typedefs.md#string_view)|Specjalizacja szablonu klasy `basic_string_view` z elementami typu **`char`** .|
|[wstring_view](../standard-library/string-view-typedefs.md#wstring_view)|Specjalizacja szablonu klasy `basic_string_view` z elementami typu **`wchar_t`** .|
|[u16string_view](../standard-library/string-view-typedefs.md#u16string_view)|Specjalizacja szablonu klasy `basic_string_view` z elementami typu **`char16_t`** .|
|[u32string_view](../standard-library/string-view-typedefs.md#u32string_view)|Specjalizacja szablonu klasy `basic_string_view` z elementami typu **`char32_t`** .|

### <a name="operators"></a>Operatory

\<string_view>Operatory mogą porównywać `string_view` obiekty z obiektami dowolnego typu ciągu z możliwością konwersji.

|Operator|Opis|
|-|-|
|[operator! =](../standard-library/string-view-operators.md#op_neq)|Testuje, czy obiekt po lewej stronie operatora nie jest równy obiektowi po prawej stronie.|
|[operator = =](../standard-library/string-view-operators.md#op_eq_eq)|Testuje, czy obiekt po lewej stronie operatora jest równy obiektowi po prawej stronie.|
|[<operatora](../standard-library/string-view-operators.md#op_lt)|Testuje, czy obiekt po lewej stronie operatora jest mniejszy od obiektu po prawej stronie.|
|[<operatora =](../standard-library/string-view-operators.md#op_lt_eq)|Testuje, czy obiekt po lewej stronie operatora jest mniejszy od lub równy obiektowi po prawej stronie.|
|[<operatora\<](../standard-library/string-view-operators.md#op_lt_lt)|Funkcja szablonu, która wstawia `string_view` do strumienia wyjściowego.|
|[>operatora](../standard-library/string-view-operators.md#op_gt)|Testuje, czy obiekt po lewej stronie operatora jest większy niż obiekt po prawej stronie.|
|[>operatora =](../standard-library/string-view-operators.md#op_gt_eq)|Testuje, czy obiekt po lewej stronie operatora jest większy niż lub równy obiektowi po prawej stronie.|

### <a name="literals"></a>Literały

|Operator|Opis|
|-|-|
|[OHR](../standard-library/string-view-operators.md#op_sv)|Tworzy `string_view` ,, `wstring_view` `u16string_view` lub `u32string_view` w zależności od typu literału ciągu, do którego jest dołączany.|

### <a name="classes"></a>Klasy

|Klasa|Opis|
|-|-|
|[Klasa basic_string_view](../standard-library/basic-string-view-class.md)|Szablon klasy, który udostępnia widok tylko do odczytu w sekwencji dowolnych obiektów podobnej do znaku.|
|[skrótu](string-view-hash.md)|Obiekt funkcyjny, który generuje wartość skrótu dla string_view.|

## <a name="requirements"></a>Wymagania

- **Nagłówek:**\<string_view>

- **Przestrzeń nazw:** std

- **Opcja kompilatora:** std: c++ 17 (lub nowsza)

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
