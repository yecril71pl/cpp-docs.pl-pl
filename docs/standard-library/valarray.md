---
title: '&lt;valarray &gt;'
ms.date: 11/04/2016
f1_keywords:
- <valarray>
helpviewer_keywords:
- valarray header
ms.assetid: 30835415-21c1-4801-8f24-6bbef7dd8ecd
ms.openlocfilehash: ed90273fe293ae2e08c3c91762c12c42bb368c16
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688761"
---
# <a name="ltvalarraygt"></a>&lt;valarray &gt;

Definiuje szablon klasy valarray i wiele pomocniczych szablonów klas i funkcji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<valarray >

**Przestrzeń nazw:** std

> [!NOTE]
> Biblioteka \<valarray > używa instrukcji "#include < initializer_list >".

## <a name="remarks"></a>Uwagi

Te szablony i funkcje klasy są dozwolone nietypowej szerokości geograficznej w celu zwiększenia wydajności. W każdym przypadku każda funkcja zwracająca typ `valarray<T1>` może zwrócić obiekt innego typu T2. W takim przypadku każda funkcja, która akceptuje jeden lub więcej argumentów typu `valarray<T2>` musi mieć przeciążenia, które akceptują dowolne kombinacje tych argumentów, z których każdy zamieniono argument typu T2.

## <a name="members"></a>Elementy członkowskie

### <a name="functions"></a>Funkcje

|||
|-|-|
|[ABS](../standard-library/valarray-functions.md#abs)|Działa na elementach wejściowych valarray, zwracając valarray, których elementy są równe wartości bezwzględnej elementów danych wejściowych valarray.|
|[Acos](../standard-library/valarray-functions.md#acos)|Działa na elementach wejściowych valarray, zwracając valarray, których elementy są równe cosinusowi elementów danych wejściowych valarray.|
|[Asin](../standard-library/valarray-functions.md#asin)|Działa na elementach wejściowych valarray, zwracając valarray, których elementy są równe sinusowi elementów danych wejściowych valarray.|
|[atan](../standard-library/valarray-functions.md#atan)|Działa na elementach wejściowych valarray, zwracając valarray, których elementy są równe wartości głównej arcus tangens elementów danych wejściowych valarray.|
|[atan2](../standard-library/valarray-functions.md#atan2)|Zwraca valarray, którego elementy są równe arcus tangens składników kartezjańskiego określonych przez kombinację stałych i elementów valarrays.|
|[zaczną](../standard-library/valarray-functions.md#begin)||
|[cosinus](../standard-library/valarray-functions.md#cos)|Działa na elementach wejściowych valarray, zwracając valarray, których elementy są równe cosinusowi elementów danych wejściowych valarray.|
|[cosh —](../standard-library/valarray-functions.md#cosh)|Działa na elementach wejściowych valarray, zwracając valarray, których elementy są równe cosinus hiperboliczny elementów danych wejściowych valarray.|
|[punktów](../standard-library/valarray-functions.md#end)||
|[EXP](../standard-library/valarray-functions.md#exp)|Działa na elementach wejściowych valarray, zwracając valarray, których elementy są równe naturalnej wykładniczej elementów danych wejściowych valarray.|
|[rejestrowane](../standard-library/valarray-functions.md#log)|Działa na elementach wejściowych valarray, zwracając valarray, których elementy są równe logarytmu naturalnego elementów danych wejściowych valarray.|
|[log10 —](../standard-library/valarray-functions.md#log10)|Działa na elementach wejściowej valarray, zwracając element valarray, którego elementy są równe 10 lub logarytmu wartości wejściowej elementów valarray.|
|[pow](../standard-library/valarray-functions.md#pow)|Działa na elementach wejściowych valarrays i stałych, zwracając valarray, których elementy są równe podstawie określonej przez elementy elementu wejściowego valarray lub stałej podniesionej do wykładnika określonego przez elementy valarray danych wejściowych lub stałego.|
|[sinus](../standard-library/valarray-functions.md#sin)|Działa na elementach wejściowych valarray, zwracając valarray, których elementy są równe sinusowi elementów danych wejściowych valarray.|
|[SINH](../standard-library/valarray-functions.md#sinh)|Działa na elementach wejściowych valarray, zwracając valarray, których elementy są równe sinus hiperboliczny elementów danych wejściowych valarray.|
|[sqrt](../standard-library/valarray-functions.md#sqrt)|Działa na elementach wejściowych valarray, zwracając valarray, których elementy są równe pierwiastek kwadratowy elementów valarray danych wejściowych.|
|[wymiany](../standard-library/valarray-functions.md#swap)||
|[Tan](../standard-library/valarray-functions.md#tan)|Działa na elementach wejściowych valarray, zwracając valarray, których elementy są równe tangensowi elementów danych wejściowych valarray.|
|[TANH —](../standard-library/valarray-functions.md#tanh)|Działa na elementach wejściowych valarray, zwracając valarray, których elementy są równe tangens hiperboliczny elementów danych wejściowych valarray.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator!=](../standard-library/valarray-operators.md#op_neq)|Testuje, czy odpowiadające elementy o dwóch równych rozmiarach valarrays są nierówne lub czy wszystkie elementy valarray są nierówne określonej wartości typu elementu valarray.|
|[zakład](../standard-library/valarray-operators.md#op_mod)|Uzyskuje resztę dzielącą odpowiadające elementy o dwóch równych rozmiarach valarrays lub dzielących valarray przez określoną wartość typu elementu valarray lub dzielącą określoną wartość przez valarray.|
|[& operatora](../standard-library/valarray-operators.md#op_amp)|Uzyskuje `AND` bitowe między odpowiadającymi im elementami o dwóch rozmiarach o rozmiarze równym valarrays lub między valarray a określoną wartością typu elementu.|
|[& operatora &](../standard-library/valarray-operators.md#op_amp_amp)|Uzyskuje `AND` logiczne między odpowiadającymi im elementami o dwóch rozmiarach o równym rozmiarze valarrays lub między valarray a określoną wartością typu elementu valarray.|
|[> operatora](../standard-library/valarray-operators.md#op_gt)|Testuje, czy elementy jednego valarray są większe niż elementy o równym rozmiarze valarray lub czy wszystkie elementy valarray są większe lub mniejsze niż określona wartość typu elementu valarray.|
|[operator>=](../standard-library/valarray-operators.md#op_gt_eq)|Testuje, czy elementy jednego valarray są większe niż lub równe elementom o równym rozmiarze valarray lub czy wszystkie elementy valarray są większe niż lub równe określonej wartości.|
|[> operatora >](../standard-library/valarray-operators.md#op_gt_gt)|Prawy przesuwa bity dla każdego elementu valarray określoną liczbę pozycji lub przez liczbę elementów określoną przez drugi valarray.|
|[< operatora](../standard-library/valarray-operators.md#op_lt)|Testuje, czy elementy jednego valarray są mniejsze niż elementy o równym rozmiarze valarray lub czy wszystkie elementy valarray są większe lub mniejsze niż określona wartość.|
|[< operatora =](../standard-library/valarray-operators.md#op_lt_eq)|Testuje, czy elementy jednego valarray są mniejsze niż lub równe elementom o równym rozmiarze valarray lub czy wszystkie elementy valarray są większe lub równe lub mniejsze lub równe określonej wartości.|
|[< operatora <](../standard-library/valarray-operators.md#op_lt_lt)|Lewy przenosi bity dla każdego elementu valarray określoną liczbę pozycji lub przez liczbę elementów określoną przez drugi valarray.|
|[zakład](../standard-library/valarray-operators.md#op_star)|Uzyskuje iloczyn elementów rzeczy między odpowiednimi elementami o rozmiarze dwóch valarrays lub między valarray a określoną wartością typu elementu valarray.|
|[operator +](../standard-library/valarray-operators.md#op_add)|Uzyskuje sumę elementów między odpowiednimi elementami o rozmiarze dwóch valarrays lub między valarray a określoną wartością typu elementu valarray.|
|[zakład](../standard-library/valarray-operators.md#operator-)|Uzyskuje różnicę elementów między odpowiednimi elementami o rozmiarze dwóch valarrays lub między valarray a określoną wartością typu elementu valarray.|
|[zakład](../standard-library/valarray-operators.md#op_div)|Uzyskuje iloraz elementów między odpowiednimi elementami o rozmiarze dwóch valarrays lub między valarray a określoną wartością typu elementu valarray.|
|[operator = =](../standard-library/valarray-operators.md#op_eq_eq)|Testuje, czy odpowiadające elementy dwóch valarrays o równym rozmiarze są równe lub czy wszystkie elementy valarray są równe określonej wartości typu elementu valarray.|
|[operator ^](../standard-library/valarray-operators.md#op_xor)|Uzyskuje bitowe `OR` wyłącznych między odpowiadającymi im elementami o rozmiarze dwóch valarrays lub między valarray a określoną wartością typu elementu.|
|[zakład&#124;](../standard-library/valarray-operators.md#op_or)|Uzyskuje `OR` bitowe między odpowiadającymi im elementami o dwóch rozmiarach o rozmiarze równym valarrays lub między valarray a określoną wartością typu elementu.|
|[zakład&#124;&#124;](../standard-library/valarray-operators.md#op_lor)|Uzyskuje `OR` logiczne między odpowiadającymi im elementami o dwóch rozmiarach o równym rozmiarze valarrays lub między valarray a określoną wartością typu elementu valarray.|

### <a name="classes"></a>Klasy

|||
|-|-|
|[gslice, klasa](../standard-library/gslice-class.md)|Klasa narzędzi do valarray, która jest używana do definiowania wielowymiarowych wycinków valarray.|
|[gslice_array, klasa](../standard-library/gslice-array-class.md)|Wewnętrzny, pomocniczy szablon klasy, który obsługuje ogólne obiekty wycinków, dostarczając operacje między tablicami podzestawu zdefiniowanymi przez ogólny wycinek elementu valarray.|
|[indirect_array, klasa](../standard-library/indirect-array-class.md)|Wewnętrzny, pomocniczy szablon klasy, który obsługuje obiekty, które są podzestawami valarrays przez dostarczanie operacji między tablicami podzestawu zdefiniowanymi przez określenie podzestawu indeksów nadrzędnego valarray.|
|[mask_array, klasa](../standard-library/mask-array-class.md)|Wewnętrzny, pomocniczy szablon klasy, który obsługuje obiekty, które są podzbiorami elementu nadrzędnego valarrays, określone za pomocą wyrażenia logicznego, dostarczając operacje między tablicami podzbioru.|
|[slice, klasa](../standard-library/slice-class.md)|Klasa narzędzi do valarray, która jest używana do definiowania jednowymiarowych podzestawów, podobne do wektora valarray.|
|[slice_array, klasa](../standard-library/slice-array-class.md)|Wewnętrzny, pomocniczy szablon klasy, który obsługuje obiekty wycinków, dostarczając operacje między tablicami podzestawu zdefiniowanymi przez wycinek elementu valarray.|
|[valarray, klasa](../standard-library/valarray-class.md)|Szablon klasy opisuje obiekt, który kontroluje sekwencję elementów typu `Type`, które są przechowywane jako tablica i zaprojektowane do wykonywania operacji matematycznych o dużej szybkości, zoptymalizowanych pod kątem wydajności obliczeniowej.|

### <a name="specializations"></a>Specjalizacje

|||
|-|-|
|[Klasa valarray \<bool >](../standard-library/valarray-bool-class.md)|Wyspecjalizowana wersja szablonu klasy valarray \<**typ**> do elementów typu **bool**.|

## <a name="see-also"></a>Zobacz także

[Odwołania do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md) \
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
