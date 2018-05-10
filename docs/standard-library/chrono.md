---
title: '&lt;chrono&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- chrono/std::chrono::nanoseconds
- chrono/std::chrono::minutes
- chrono/std::chrono::seconds
- <chrono>
- chrono/std::chrono::hours
- chrono/std::chrono::milliseconds
- chrono/std::chrono::microseconds
dev_langs:
- C++
ms.assetid: 844de749-f306-482e-89bc-6f53c99c8324
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d701b290100f812f3c7845096960561cb101472
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="ltchronogt"></a>&lt;chrono&gt;

Dołącz nagłówek standardowy \<chrono > Aby zdefiniować klasy i funkcje, które reprezentują i modyfikowania okresach czasu i czasie czasu.

Począwszy od programu Visual Studio 2015, implementacja `steady_clock` został zmieniony w celu spełnienia wymagań C++ Standard opanowanie i monotonicity. `steady_clock` teraz jest oparta na QueryPerformanceCounter() i `high_resolution_clock` jest teraz typedef dla `steady_clock`. W związku z tym w programie Visual C++ `steady_clock::time_point` jest teraz typedef dla `chrono::time_point<steady_clock>`, jednak nie jest w przypadku innych implementacji.

## <a name="syntax"></a>Składnia

```cpp
#include <chrono>
```

### <a name="classes"></a>Klasy

|Nazwa|Opis|
|----------|-----------------|
|[duration, klasa](../standard-library/duration-class.md)|Opisuje typ, który przechowuje przedział czasu.|
|[time_point, klasa](../standard-library/time-point-class.md)|Opisuje typ, który reprezentuje punkt w czasie.|

### <a name="structs"></a>Struktury

|Nazwa|Opis|
|----------|-----------------|
|[common_type, struktura](../standard-library/common-type-structure.md)|W tym artykule opisano specjalizacji szablonu klasy [common_type —](../standard-library/common-type-class.md) dla wystąpień elementu `duration` i `time_point`.|
|[duration_values, struktura](../standard-library/duration-values-structure.md)|Udostępnia wartości określonej dla `duration` parametr szablonu `Rep`.|
|[steady_clock, struktura](../standard-library/steady-clock-struct.md)|Reprezentuje `steady` zegara.|
|[system_clock, struktura](../standard-library/system-clock-structure.md)|Reprezentuje *typ zegara* opartego na zegarze w czasie rzeczywistym systemu.|
|[treat_as_floating_point, struktura](../standard-library/treat-as-floating-point-structure.md)|Określa, czy typem może być traktowana jako typ zmiennoprzecinkowy.|

### <a name="functions"></a>Funkcje

|Nazwa|Opis|
|----------|-----------------|
|[duration_cast](../standard-library/chrono-functions.md#duration_cast)|Rzutowania `duration` obiektu określonego typu.|
|[time_point_cast](../standard-library/chrono-functions.md#time_point_cast)|Rzutowania `time_point` obiektu określonego typu.|

### <a name="operators"></a>Operatory

|Nazwa|Opis|
|----------|-----------------|
|[operator-](../standard-library/chrono-operators.md#operator-)|Operator odejmowania lub Negacja `duration` i `time_point` obiektów.|
|[operator!=](../standard-library/chrono-operators.md#op_neq)|Operator nierówności, który jest używany z `duration` lub `time_point` obiektów.|
|[Operator modulo](../standard-library/chrono-operators.md#op_modulo)|Operator modulo operacje na `duration` obiektów.|
|[operator *](../standard-library/chrono-operators.md#op_star)|Operator mnożenia dla `duration` obiektów.|
|[operator /](../standard-library/chrono-operators.md#op_div)|Operator dzielenia dla `duration` obiektów.|
|[operator +](../standard-library/chrono-operators.md#op_add)|Dodaje `duration` i `time_point` obiektów.|
|[Operator&lt;](../standard-library/chrono-operators.md#op_lt)|Określa, czy co najmniej `duration` lub `time_point` obiekt jest mniejszy niż innego `duration` lub `time_point` obiektu.|
|[Operator&lt;=](../standard-library/chrono-operators.md#op_lt_eq)|Określa, czy co najmniej `duration` lub `time_point` obiekt jest mniejszy niż lub równy do innego `duration` lub `time_point` obiektu.|
|[operator==](../standard-library/chrono-operators.md#op_eq_eq)|Określa, czy dwa `duration` reprezentować przedziały czasu, które mają taką samą długość lub czy dwa `time_point` obiekty reprezentują tego samego punktu w czasie.|
|[Operator&gt;](../standard-library/chrono-operators.md#op_gt)|Określa, czy co najmniej `duration` lub `time_point` obiekt jest większy niż innego `duration` lub `time_point` obiektu.|
|[Operator&gt;=](../standard-library/chrono-operators.md#op_gt_eq)|Określa, czy co najmniej `duration` lub `time_point` obiektu jest większa lub równa innej `duration` lub `time_point` obiektu.|

### <a name="predefined-duration-types"></a>Typy wstępnie zdefiniowanego czasu trwania

Aby uzyskać więcej informacji o typach stosunek, które są używane w następujących definicje typów, zobacz [ \<stosunek >](../standard-library/ratio.md).

|Element TypeDef|Opis|
|-------------|-----------------|
|`typedef duration<long long, nano> nanoseconds;`|Synonim `duration` typu, który ma jeden nanosekund okres znaczników.|
|`typedef duration<long long, micro> microseconds;`|Synonim `duration` typu, który ma jeden mikrosekund okres znaczników.|
|`typedef duration<long long, milli> milliseconds;`|Synonim `duration` typu, który ma okres znaczników jednej milisekundy.|
|`typedef duration<long long> seconds;`|Synonim `duration` typu, który ma okres znaczników jednej sekundzie.|
|`typedef duration<int, ratio<60> > minutes;`|Synonim `duration` typu, który ma okres znaczników jednej minuty.|
|`typedef duration<int, ratio<3600> > hours;`|Synonim `duration` typu, który ma okres znaczników jedną godzinę.|

### <a name="literals"></a>Literały

**(C ++ 11)**  \<Chrono > nagłówka definiuje następujące [literały definiowane przez użytkownika](../cpp/user-defined-literals-cpp.md) można większa wygody, bezpieczeństwo typów i utrzymanie kodu. Literały te są zdefiniowane w `literals::chrono_literals` wbudowanego obszaru nazw i czy w zakres, kiedy std::chrono znajduje się w zakresie.

|Literału|Opis|
|-------------|-----------------|
|chrono::hours operator "" h (Val długi czas bez znaku)|Określa godzin jako wartości całkowite.|
|chrono::duration\<dwa razy, współczynnik\<3600 >> operator "" h (Val podwójnej długości)|Określa godzin jako wartości zmiennoprzecinkowej.|
|chrono::minutes (operator "" min) (wartość długo długa bez znaku)|Określa w minutach jako wartością całkowitą.|
|chrono::duration\<dwa razy, współczynnik\<60 >> (operator "" min) (liczba typu double Val)|Określa w minutach, jako wartość zmiennoprzecinkowa.|
|chrono::seconds operator "" s (Val długi czas bez znaku)|Określa w minutach jako wartością całkowitą.|
|chrono::duration\<podwójne > — operator "" s (Val podwójnej długości)|Określa w sekundach, jako wartość zmiennoprzecinkowa.|
|chrono::milliseconds operator "" ms (Val długi czas bez znaku)|Określa w milisekundach jako wartością całkowitą.|
|chrono::duration\<dwa razy, milli > — operator "" ms (Val podwójnej długości)|Określa w milisekundach jako wartość zmiennoprzecinkową.|
|chrono::microseconds operator "" nam (Val długi czas bez znaku)|Określa mikrosekundach jako wartością całkowitą.|
|chrono::duration\<dwa razy, micro > — operator "" nam (Val podwójnej długości)|Określa mikrosekundach jako wartość zmiennoprzecinkową.|
|chrono::nanoseconds operator "" ns (Val długi czas bez znaku)|Określa nanosekundach jako wartością całkowitą.|
|chrono::duration\<dwa razy, nano > — operator "" ns (Val podwójnej długości)|Określa nanosekundach jako wartość zmiennoprzecinkową.|
|||

Następujące przykłady przedstawiają sposób użycia literały chrono.

```cpp
constexpr auto day = 24h;
constexpr auto week = 24h* 7;
constexpr auto my_duration_unit = 108ms;
```

## <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
