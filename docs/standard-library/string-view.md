---
title: '&lt;string_view&gt;'
ms.date: 04/18/2019
helpviewer_keywords:
- string_view header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
ms.openlocfilehash: 8952416cf37fc4d8d281d6ced9b8264495ec3799
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346648"
---
# <a name="ltstringviewgt"></a>&lt;string_view&gt;

Określa szablon klasy `basic_string_view` i pokrewne typy i operatorów. (Wymaga opcji kompilatora [STD: c ++ 17](../build/reference/std-specify-language-standard-version.md) lub nowszej.)

## <a name="syntax"></a>Składnia

```cpp
#include <string_view>
```

## <a name="remarks"></a>Uwagi

Rodzina string_view specjalizacje szablonu zawiera wydajnym sposobem przekazywania uchwyt tylko do odczytu, bezpieczne pod względem wyjątków, nie będącej właścicielem do danych znakowych żadnych obiektów jak ciąg od pierwszego elementu w sekwencji na pozycji zero. Parametr funkcji typu `string_view` (czyli element typedef dla `basic_string_view<char>`) takich jak akceptuje argumentów `std::string`, **char\***, lub inne klasy przypominającej ciągu wąskiego znaków, dla którego niejawne Konwersja na `string_view` jest zdefiniowana. Podobnie, parametr `wstring_view`, `u16string_view` lub `u32string_view` może akceptować dowolny typ string, dla którego zdefiniowano niejawną konwersję. Aby uzyskać więcej informacji, zobacz [basic_string_view klasy](../standard-library/basic-string-view-class.md).

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[string_view](../standard-library/string-view-typedefs.md#string_view)|Specjalizacja szablonu klasy `basic_string_view` elementami typu **char**.|
|[wstring_view](../standard-library/string-view-typedefs.md#wstring_view)|Specjalizacja szablonu klasy `basic_string_view` elementami typu **wchar_t**.|
|[u16string_view](../standard-library/string-view-typedefs.md#u16string_view)|Specjalizacja szablonu klasy `basic_string_view` elementami typu `char16_t`.|
|[u32string_view](../standard-library/string-view-typedefs.md#u32string_view)|Specjalizacja szablonu klasy `basic_string_view` elementami typu `char32_t`.|

### <a name="operators"></a>Operatory

\<String_view > operatorów można porównać `string_view` obiekty do obiektów przekonwertować żadnych typów ciągów.

|Operator|Opis|
|-|-|
|[operator!=](../standard-library/string-view-operators.md#op_neq)|Sprawdza, czy obiekt po lewej stronie operatora nie jest równy obiektowi po prawej stronie.|
|[operator==](../standard-library/string-view-operators.md#op_eq_eq)|Sprawdza, czy obiekt po lewej stronie operatora jest równy obiektowi po prawej stronie.|
|[Operator <](../standard-library/string-view-operators.md#op_lt)|Sprawdza, czy obiekt po lewej stronie operatora jest mniejszy niż do obiektu po prawej stronie.|
|[Operator < =](../standard-library/string-view-operators.md#op_lt_eq)|Sprawdza, czy obiekt po lewej stronie operatora jest mniejszy niż lub równy obiektowi po prawej stronie.|
|[Operator <\<](../standard-library/string-view-operators.md#op_lt_lt)|Funkcja szablonu, który wstawia `string_view` do strumienia wyjściowego.|
|[operator>](../standard-library/string-view-operators.md#op_gt)|Sprawdza, czy obiekt po lewej stronie operatora jest większy niż obiekt po prawej stronie.|
|[operator>=](../standard-library/string-view-operators.md#op_gt_eq)|Sprawdza, czy obiekt po lewej stronie operatora jest większy lub równy obiektowi po prawej stronie.|

### <a name="literals"></a>Literały

|Operator|Opis|
|-|-|
|[sv](../standard-library/string-view-operators.md#op_sv)|Konstruuje `string_view`, `wstring_view`, `u16string_view`, lub `u32string_view` w zależności od typu literału ciągu, do którego jest dołączona.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[basic_string_view, klasa](../standard-library/basic-string-view-class.md)|Szablon klasy, który służy do wyświetlania tylko do odczytu do dowolnych obiektów przypominające znak sekwencji.|
|[hash](string-view-hash.md)|Obiekt funkcji, która generuje wartość skrótu dla string_view.|

## <a name="requirements"></a>Wymagania

- **Nagłówek:** \<string_view >

- **Namespace:** standardowe

- **— Opcja kompilatora:** STD: c ++ 17 (lub nowszy)

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
