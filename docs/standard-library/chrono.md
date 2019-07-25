---
title: '&lt;Chrono&gt;'
ms.date: 05/07/2019
f1_keywords:
- chrono/std::chrono::nanoseconds
- chrono/std::chrono::minutes
- chrono/std::chrono::seconds
- <chrono>
- chrono/std::chrono::hours
- chrono/std::chrono::milliseconds
- chrono/std::chrono::microseconds
ms.assetid: 844de749-f306-482e-89bc-6f53c99c8324
ms.openlocfilehash: f01b00a1469cdf82590a1bdfc742312ec96912c9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459450"
---
# <a name="ltchronogt"></a>&lt;Chrono&gt;

Uwzględnij standardowy nagłówek \<Chrono >, aby definiować klasy i funkcje, które reprezentują i manipulowanie okresami czasowymi i czasem.

Począwszy od programu Visual Studio 2015, implementacja programu `steady_clock` została zmieniona tak, aby C++ spełniała standardowe wymagania dotyczące stałego i monotonicity. `steady_clock`jest teraz oparta na QueryPerformanceCounter () i `high_resolution_clock` jest teraz elementem TypeDef dla `steady_clock`. W związku z tym, w C++ kompilatorze `steady_clock::time_point` Microsoft jest teraz elementem TypeDef `chrono::time_point<steady_clock>`dla, jednak ta reguła nie jest konieczna dla innych implementacji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<Chrono >

**Przestrzeń nazw:** std

## <a name="members"></a>Elementy członkowskie

### <a name="classes"></a>Klasy

|||
|-|-|
|[duration, klasa](../standard-library/duration-class.md)|Opisuje typ, który przechowuje przedział czasu.|
|[time_point, klasa](../standard-library/time-point-class.md)|Opisuje typ, który reprezentuje punkt w czasie.|

### <a name="structs"></a>Struktury

|||
|-|-|
|[common_type, struktura](../standard-library/common-type-structure.md)|Opisuje specjalizacje klasy szablonu [common_type](../standard-library/common-type-class.md) dla wystąpień `duration` i. `time_point`|
|[duration_values, struktura](../standard-library/duration-values-structure.md)|Zawiera określone wartości dla `duration` parametru `Rep`szablonu.|
|[high_resolution_clock, struktura](../standard-library/high-resolution-clock-struct.md)||
|[steady_clock, struktura](../standard-library/steady-clock-struct.md)|`steady` Przedstawia zegar.|
|[system_clock, struktura](../standard-library/system-clock-structure.md)|Reprezentuje *Typ zegara* , który jest oparty na zegarze w czasie rzeczywistym systemu.|
|[treat_as_floating_point, struktura](../standard-library/treat-as-floating-point-structure.md)|Określa, czy typ może być traktowany jako typ zmiennoprzecinkowy.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[duration_cast](../standard-library/chrono-functions.md#duration_cast)|Rzutuje `duration` obiekt na określony typ.|
|[time_point_cast](../standard-library/chrono-functions.md#time_point_cast)|Rzutuje `time_point` obiekt na określony typ.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[zakład](../standard-library/chrono-operators.md#operator-)|Operator odejmowania lub negacji `duration` obiektów i. `time_point`|
|[operator!=](../standard-library/chrono-operators.md#op_neq)|Operator nierówności używany z `duration` lub `time_point` obiektami.|
|[modulo operatorów](../standard-library/chrono-operators.md#op_modulo)|Operator dla operacji modulo `duration` na obiektach.|
|[zakład](../standard-library/chrono-operators.md#op_star)|Operator mnożenia dla `duration` obiektów.|
|[zakład](../standard-library/chrono-operators.md#op_div)|Operator dzielenia dla `duration` obiektów.|
|[operator +](../standard-library/chrono-operators.md#op_add)|Dodaje `duration` obiekty `time_point` i.|
|[zakład&lt;](../standard-library/chrono-operators.md#op_lt)|Określa, czy `duration` jeden `time_point` lub obiekt jest mniejszy niż `duration` inny `time_point` obiekt lub.|
|[zakład&lt;=](../standard-library/chrono-operators.md#op_lt_eq)|Określa, czy `duration` jeden `time_point` lub obiekt jest mniejszy lub równy innemu `duration` lub `time_point` obiektowi.|
|[operator==](../standard-library/chrono-operators.md#op_eq_eq)|Określa, czy `duration` dwa obiekty reprezentują przedziały czasu mające taką samą długość, `time_point` czy dwa obiekty reprezentują ten sam punkt w czasie.|
|[zakład&gt;](../standard-library/chrono-operators.md#op_gt)|Określa, czy `duration` jeden `time_point` lub obiekt jest większy niż `duration` inny `time_point` obiekt lub.|
|[zakład&gt;=](../standard-library/chrono-operators.md#op_gt_eq)|Określa, czy `duration` jeden `time_point` lub obiekt jest większy lub równy innemu `duration` lub `time_point` obiektowi.|

### <a name="typedefs-predefined-duration-types"></a>Typedefs (wstępnie zdefiniowane typy czasu trwania)

Aby uzyskać więcej informacji na temat typów współczynników, które są używane w następujących elementach typedef, zobacz [ \<współczynnik >](../standard-library/ratio.md).

||| ||| | `typedef duration<long long, nano> nanoseconds;`| Synonim dla `duration` typu, który ma wartość o długości taktu 1 nanosekund. |`typedef duration<long long, micro> microseconds;`| | Synonim dla `duration` typu, który ma wartość 1 mikrosekundowych.`typedef duration<long long, milli> milliseconds;`| | | Synonim dla `duration` typu, który ma wartość 1 milisekund. | |`typedef duration<long long> seconds;`| Synonim dla `duration` typu, który ma wartość o skali 1 sekundy. | |`typedef duration<int, ratio<60> > minutes;`| Synonim dla `duration` typu, który ma interwał o wartości 1 minuty. | |`typedef duration<int, ratio<3600> > hours;`| Synonim dla `duration` typu, który ma godzinę 1 godziny. |

### <a name="literals"></a>Literały

**(C++ 11)** Nagłówek > Chrono definiuje następujące literały [zdefiniowane przez użytkownika](../cpp/user-defined-literals-cpp.md) , których można użyć w celu uzyskania większej wygody, bezpieczeństwa typów i utrzymania kodu. \< Te literały są zdefiniowane w `literals::chrono_literals` wbudowanej przestrzeni nazw i znajdują się w zakresie, gdy std:: chrono znajduje się w zakresie.

|||
|-|-|
|operator godzin "" h (bez znaku long long Val)|Określa godziny jako wartość całkowitą.|
|czas\<trwania Double,\<współczynnik 3600 > > operator "" h (long double Val)|Określa godziny jako wartość zmiennoprzecinkową.|
|minuty (operator "min") (bez znaku long long Val)|Określa liczbę minut jako wartość całkowitą.|
|czas\<trwania Double,\<stosunek 60 > > (operator "" min) (long double Val)|Określa liczbę minut jako wartość zmiennoprzecinkową.|
|operator sekund "" s (bez znaku long long Val)|Określa liczbę minut jako wartość całkowitą.|
|operator\<podwójnego > czasu trwania "" s (long double Val)|Określa liczbę sekund jako wartość zmiennoprzecinkową.|
|milisekundy operatora "" MS (bez znaku long long Val)|Określa milisekundy jako wartość całkowitą.|
|czas\<trwania Double, Milli > operator "" MS (long double Val)|Określa milisekundy jako wartość zmiennoprzecinkową.|
|operator mikrosekund "" US (bez znaku long long Val)|Określa mikrosekundy jako wartość całkowitą.|
|czas\<trwania Double, Micro > operator "" US (long double Val)|Określa mikrosekund jako wartość zmiennoprzecinkową.|
|operator nanosekund "" NS (bez znaku long long Val)|Określa liczbę nanosekund jako wartość całkowitą.|
|czas\<trwania Double, Nano > operator "" NS (long double Val)|Określa liczbę nanosekund jako wartość zmiennoprzecinkową.|

W poniższych przykładach pokazano, jak używać literałów Chrono.

```cpp
constexpr auto day = 24h;
constexpr auto week = 24h* 7;
constexpr auto my_duration_unit = 108ms;
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
