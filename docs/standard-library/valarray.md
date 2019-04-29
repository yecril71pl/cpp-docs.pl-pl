---
title: '&lt;valarray&gt;'
ms.date: 11/04/2016
f1_keywords:
- <valarray>
helpviewer_keywords:
- valarray header
ms.assetid: 30835415-21c1-4801-8f24-6bbef7dd8ecd
ms.openlocfilehash: 8b8118722d7219e3b30e11ad67411595c3dc36ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62365419"
---
# <a name="ltvalarraygt"></a>&lt;valarray&gt;

Definiuje valarray klasy szablonu i wiele pomocniczych szablonu klasy i funkcje.

## <a name="syntax"></a>Składnia

```cpp
#include <valarray>
```

## <a name="remarks"></a>Uwagi

Te klasy szablonów i funkcje są dozwolone nietypowe szerokości geograficznej w celu poprawy wydajności. W szczególności żadnej funkcji, zwracająca typ `valarray<T1>` może zwrócić obiekt innego typu T2. W takim przypadku funkcji, które przyjmuje jeden lub więcej argumentów typu `valarray<T2>` musi mieć przeciążenia, które akceptują dowolnej kombinacji tych argumentów, każdy zastąpiona argumentu typu T2.

### <a name="functions"></a>Funkcje

|Funkcja|Opis|
|-|-|
|[abs](../standard-library/valarray-functions.md#abs)|Działa na elementy wejściowe tablicy valarray, zwracając valarray, której elementy są równe wartość bezwzględną liczby elementów tworzonej tablicy valarray danych wejściowych.|
|[ACOS](../standard-library/valarray-functions.md#acos)|Działa na elementy wejściowe tablicy valarray, zwracając valarray, której elementy są równe arcus cosinus liczby elementów tworzonej tablicy valarray danych wejściowych.|
|[ASIN](../standard-library/valarray-functions.md#asin)|Działa na elementy wejściowe tablicy valarray, zwracając valarray, której elementy są równe arcus sinus liczby elementów tworzonej tablicy valarray danych wejściowych.|
|[atan](../standard-library/valarray-functions.md#atan)|Działa na elementy wejściowe tablicy valarray, zwracając valarray, której elementy są równe wartość główną wartości arcus tangens elementów tworzonej tablicy valarray danych wejściowych.|
|[atan2](../standard-library/valarray-functions.md#atan2)|Zwraca tablicę valarray, której elementy są równe arcus tangens Kartezjańskiego określone przez kombinację stałych i elementy valarrays składników.|
|[cos](../standard-library/valarray-functions.md#cos)|Działa na elementy wejściowe tablicy valarray, zwracając valarray, której elementy są równe cosinus liczby elementów tworzonej tablicy valarray danych wejściowych.|
|[cosh](../standard-library/valarray-functions.md#cosh)|Działa na elementy wejściowe tablicy valarray, zwracając valarray, której elementy są równe cosinus hiperboliczny liczby elementów tworzonej tablicy valarray danych wejściowych.|
|[exp](../standard-library/valarray-functions.md#exp)|Działa na elementy wejściowe tablicy valarray, zwracając valarray, której elementy są równe do naturalnym wykładniczą elementów tworzonej tablicy valarray danych wejściowych.|
|[log](../standard-library/valarray-functions.md#log)|Działa na elementy wejściowe tablicy valarray, zwracając valarray, której elementy są równe logarytm naturalny elementów tworzonej tablicy valarray danych wejściowych.|
|[log10](../standard-library/valarray-functions.md#log10)|Działa na elementy wejściowe tablicy valarray, zwracając valarray, której elementy są równe, na podstawie 10 lub logarytmu elementów wejściowych tablicy valarray.|
|[Pow](../standard-library/valarray-functions.md#pow)|Działa w przypadku elementów wejściowych valarrays i stałe, zwracając valarray, której elementy są równe podstawowy określonej przez elementy wejściowe tablicy valarray lub stałą podniesioną do potęgi określonej przez elementy wejściowe tablicy valarray lub stała.|
|[sin](../standard-library/valarray-functions.md#sin)|Działa na elementy wejściowe tablicy valarray, zwracając valarray, której elementy są równe sinus elementów tworzonej tablicy valarray danych wejściowych.|
|[SINH](../standard-library/valarray-functions.md#sinh)|Działa na elementy wejściowe tablicy valarray, zwracając valarray, której elementy są równe sinus hiperboliczny liczby elementów tworzonej tablicy valarray danych wejściowych.|
|[sqrt](../standard-library/valarray-functions.md#sqrt)|Działa na elementy wejściowe tablicy valarray, zwracając valarray, której elementy są równe pierwiastek kwadratowy liczby elementów tworzonej tablicy valarray danych wejściowych.|
|[swap](../standard-library/valarray-functions.md#swap)||
|[tan](../standard-library/valarray-functions.md#tan)|Działa na elementy wejściowe tablicy valarray, zwracając valarray, której elementy są równe tangens elementów tworzonej tablicy valarray danych wejściowych.|
|[tanh](../standard-library/valarray-functions.md#tanh)|Działa na elementy wejściowe tablicy valarray, zwracając valarray, której elementy są równe tangens hiperboliczny liczby elementów tworzonej tablicy valarray danych wejściowych.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator!=](../standard-library/valarray-operators.md#op_neq)|Sprawdza, czy odpowiadające elementy dwóch valarrays równej wielkości są różne lub tego, czy wszystkie elementy tablicy valarray są nierówne określoną wartość typ elementu tablicy valarray.|
|[operator%](../standard-library/valarray-operators.md#op_mod)|Uzyskuje resztę z dzielenia odpowiadające elementy dwóch valarrays równej wielkości lub podzielenie tablicę valarray przez określoną wartość, typ elementu tablicy valarray lub podzielenie określonej wartości w tablicy valarray.|
|[Operator &](../standard-library/valarray-operators.md#op_amp)|Uzyskuje bitowe `AND` między odpowiadające elementy dwóch valarrays równej wielkości lub tablicę valarray i określoną wartość typu elementu.|
|[Operator & &](../standard-library/valarray-operators.md#op_amp_amp)|Uzyskuje logicznej `AND` między odpowiadające elementy dwóch valarrays równej wielkości lub tablicę valarray i określoną wartość typ elementu tablicy valarray.|
|[operator>](../standard-library/valarray-operators.md#op_gt)|Sprawdza, czy elementów tworzonej tablicy valarray jednego są większe niż elementów równej wielkości tablicy valarray lub tego, czy wszystkie elementy tablicy valarray jest większa lub mniejsza niż określona wartość typ elementu tablicy valarray.|
|[operator>=](../standard-library/valarray-operators.md#op_gt_eq)|Sprawdza, czy elementów tworzonej tablicy valarray jednego są większe niż lub równa elementy równej wielkości tablicy valarray lub tego, czy wszystkie elementy tablicy valarray są większe niż lub równe lub mniejsze niż lub równa określonej wartości.|
|[operator>>](../standard-library/valarray-operators.md#op_gt_gt)|Po prawej stronie przesunięcia bitów dla każdego elementu tablicy valarray określoną liczbę pozycji i według określonej ilości element-wise określony przez drugi tablicy valarray.|
|[Operator <](../standard-library/valarray-operators.md#op_lt)|Sprawdza, czy elementów tworzonej tablicy valarray jednego są mniejsze niż elementów równej wielkości tablicy valarray lub tego, czy wszystkie elementy tablicy valarray jest większa lub mniejsza niż określona wartość.|
|[Operator < =](../standard-library/valarray-operators.md#op_lt_eq)|Sprawdza, czy elementów tworzonej tablicy valarray jednego są mniejsze niż lub równe elementów tworzonej tablicy valarray równej wielkości, czy wszystkie elementy tablicy valarray są większe niż lub równe lub mniejsze niż lub równa określonej wartości.|
|[Operator <<](../standard-library/valarray-operators.md#op_lt_lt)|Po lewej stronie wykonuje przesunięcie bitów dla każdego elementu tablicy valarray określoną liczbę pozycji i według określonej ilości element-wise określony przez drugi tablicy valarray.|
|[operator*](../standard-library/valarray-operators.md#op_star)|Uzyskuje mnożenia między odpowiadające elementy dwóch valarrays równej wielkości lub z między valarray określoną wartość typ elementu tablicy valarray.|
|[operator +](../standard-library/valarray-operators.md#op_add)|Uzyskuje element-wise Suma między odpowiadające elementy dwóch valarrays równej wielkości lub z między valarray określoną wartość typ elementu tablicy valarray.|
|[operator-](../standard-library/valarray-operators.md#operator-)|Uzyskuje element-wise różnica między odpowiadające elementy dwóch valarrays równej wielkości lub z między valarray określoną wartość typ elementu tablicy valarray.|
|[operator/](../standard-library/valarray-operators.md#op_div)|Uzyskuje element-wise iloraz między odpowiadające elementy dwóch valarrays równej wielkości lub z między valarray określoną wartość typ elementu tablicy valarray.|
|[operator==](../standard-library/valarray-operators.md#op_eq_eq)|Testy czy odpowiadające elementy dwóch valarrays równej wielkości są równe, lub czy są wszystkie elementy tablicy valarray równa określonej wartości typu elementu tablicy valarray.|
|[operator^](../standard-library/valarray-operators.md#op_xor)|Uzyskuje wyłączny sumy bitowej `OR` między odpowiadające elementy dwóch valarrays równej wielkości lub tablicę valarray i określoną wartość typu elementu.|
|[operator&#124;](../standard-library/valarray-operators.md#op_or)|Uzyskuje bitowe `OR` między odpowiadające elementy dwóch valarrays równej wielkości lub tablicę valarray i określoną wartość typu elementu.|
|[operator&#124;&#124;](../standard-library/valarray-operators.md#op_lor)|Uzyskuje logicznej `OR` między odpowiadające elementy dwóch valarrays równej wielkości lub tablicę valarray i określoną wartość typ elementu tablicy valarray.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[gslice, klasa](../standard-library/gslice-class.md)|Klasy narzędzi do tablicy valarray, który jest używany do definiowania wycinków wielowymiarowej tablicy valarray.|
|[gslice_array, klasa](../standard-library/gslice-array-class.md)|Klasy wewnętrzne, pomocnicze w ramach szablonu, która obsługuje obiekty wycinek ogólne, zapewniając operacji między macierzami podzbioru zdefiniowanych przez ogólne wycinek tablicy valarray.|
|[indirect_array, klasa](../standard-library/indirect-array-class.md)|Klasa szablonu wewnętrznego, pomocnicza, która obiektów obsługuje, które są podzbiorem valarrays, zapewniając operacji między macierzami podzbioru definiowaną przez określenie podzbiór indeksów valarray nadrzędnej.|
|[mask_array, klasa](../standard-library/mask-array-class.md)|Klasa szablonu pomocnicze, wewnętrzne, który obiektów obsługuje, które są podzbiorem valarrays nadrzędnego, określony za pomocą wyrażenie logiczne, zapewniając operacji między macierzami podzbioru.|
|[slice, klasa](../standard-library/slice-class.md)|Klasy narzędzi do tablicy valarray, który jest używany do definiowania jednowymiarowo, podobne do wektora podzbiór tablicy valarray.|
|[slice_array, klasa](../standard-library/slice-array-class.md)|Klasy wewnętrzne, pomocnicze w ramach szablonu, która obsługuje obiekty wycinek, zapewniając operacji między macierzami z podzbioru zdefiniowanych przez wycinek tablicy valarray.|
|[valarray, klasa](../standard-library/valarray-class.md)|Klasa szablonu opisuje obiekt, który kontroluje sekwencje elementów typu `Type` są przechowywane w postaci tablicy oraz przeznaczony do przeprowadzania szybkich operacji matematycznych, zoptymalizowana pod kątem wydajności obliczeniowej.|

### <a name="specializations"></a>Specjalizacje

|||
|-|-|
|[valarray\<bool> Class](../standard-library/valarray-bool-class.md)|Specjalizowanej wersji szablonu valarray klasy\<**typu**> do elementów typu **bool**.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
