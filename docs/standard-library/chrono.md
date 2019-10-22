---
title: '&lt;chrono &gt;'
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
ms.openlocfilehash: e27ff146c75da6e90e6336106beba714dbe7c8a8
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689876"
---
# <a name="ltchronogt"></a>&lt;chrono &gt;

Dołącz standardowy nagłówek \<chrono >, aby zdefiniować klasy i funkcje, które reprezentują i manipulowanie okresami czasowymi i czasem.

Począwszy od programu Visual Studio 2015, implementacja `steady_clock` została zmieniona tak, aby spełniała C++ standardowe wymagania dotyczące stałego i monotonicity. `steady_clock` jest teraz oparta na QueryPerformanceCounter () i `high_resolution_clock` jest teraz elementem TypeDef dla `steady_clock`. W związku z tym w `steady_clock::time_point` kompilatora C++ Microsoft jest teraz elementem typedef dla `chrono::time_point<steady_clock>`; Jednak ta zasada nie jest konieczna w przypadku innych implementacji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<chrono >

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
|[common_type, struktura](../standard-library/common-type-structure.md)|Opisuje specjalizacje szablonu klasy [common_type](../standard-library/common-type-class.md) dla wystąpień `duration` i `time_point`.|
|[duration_values, struktura](../standard-library/duration-values-structure.md)|Udostępnia określone wartości dla `duration` parametru szablonu `Rep`.|
|[high_resolution_clock, struktura](../standard-library/high-resolution-clock-struct.md)||
|[steady_clock, struktura](../standard-library/steady-clock-struct.md)|Przedstawia zegar `steady`.|
|[system_clock, struktura](../standard-library/system-clock-structure.md)|Reprezentuje *Typ zegara* , który jest oparty na zegarze w czasie rzeczywistym systemu.|
|[treat_as_floating_point, struktura](../standard-library/treat-as-floating-point-structure.md)|Określa, czy typ może być traktowany jako typ zmiennoprzecinkowy.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[duration_cast](../standard-library/chrono-functions.md#duration_cast)|Rzutuje obiekt `duration` na określony typ.|
|[time_point_cast](../standard-library/chrono-functions.md#time_point_cast)|Rzutuje obiekt `time_point` na określony typ.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[zakład](../standard-library/chrono-operators.md#operator-)|Operator odejmowania lub negacji obiektów `duration` i `time_point`.|
|[operator!=](../standard-library/chrono-operators.md#op_neq)|Operator nierówności używany z obiektami `duration` lub `time_point`.|
|[modulo operatorów](../standard-library/chrono-operators.md#op_modulo)|Operator operacji modulo na obiektach `duration`.|
|[zakład](../standard-library/chrono-operators.md#op_star)|Operator mnożenia dla obiektów `duration`.|
|[zakład](../standard-library/chrono-operators.md#op_div)|Operator dzielenia dla `duration` obiektów.|
|[operator +](../standard-library/chrono-operators.md#op_add)|Dodaje `duration` i `time_point` obiektów.|
|[&lt; operatora](../standard-library/chrono-operators.md#op_lt)|Określa, czy jeden obiekt `duration` lub `time_point` jest mniejszy niż inny obiekt `duration` lub `time_point`.|
|[&lt; operatora =](../standard-library/chrono-operators.md#op_lt_eq)|Określa, czy jeden `duration` lub `time_point` obiekt jest mniejszy lub równy innemu `duration` lub `time_point` obiektu.|
|[operator = =](../standard-library/chrono-operators.md#op_eq_eq)|Określa, czy dwa `duration` obiekty reprezentują przedziały czasu mające taką samą długość, czy dwa obiekty `time_point` reprezentują ten sam punkt w czasie.|
|[&gt; operatora](../standard-library/chrono-operators.md#op_gt)|Określa, czy jeden obiekt `duration` lub `time_point` jest większy niż inny obiekt `duration` lub `time_point`.|
|[&gt; operatora =](../standard-library/chrono-operators.md#op_gt_eq)|Określa, czy jeden `duration` lub `time_point` obiekt jest większy lub równy innemu `duration` lub `time_point` obiekt.|

### <a name="typedefs-predefined-duration-types"></a>Typedefs (wstępnie zdefiniowane typy czasu trwania)

Aby uzyskać więcej informacji na temat typów współczynników, które są używane w następujących elementach typedef, zobacz [\<ratio >](../standard-library/ratio.md).

|||
|-|-|
|`typedef duration<long long, nano> nanoseconds;`|Synonim dla typu `duration`, który ma okres taktu 1 nanosekund.|
|`typedef duration<long long, micro> microseconds;`|Synonim dla typu `duration`, który ma okres taktu 1 mikrosekundowych.|
|`typedef duration<long long, milli> milliseconds;`|Synonim dla typu `duration`, który ma okres taktu 1 milisekundy.|
|`typedef duration<long long> seconds;`|Synonim dla typu `duration`, który ma okres taktu 1 sekundy.|
|`typedef duration<int, ratio<60> > minutes;`|Synonim dla typu `duration`, który ma interwał o wartości 1 minuty.|
|`typedef duration<int, ratio<3600> > hours;`|Synonim dla typu `duration`, który ma godzinę 1 godziny.|

### <a name="literals"></a>Literały

**(C++ 11)** Nagłówek \<chrono > definiuje następujące [literały zdefiniowane przez użytkownika](../cpp/user-defined-literals-cpp.md) , których można użyć w celu uzyskania większej wygody, bezpieczeństwa typów i utrzymania kodu. Te literały są zdefiniowane w `literals::chrono_literals` wbudowanej przestrzeni nazw i znajdują się w zakresie, gdy std:: chrono znajduje się w zakresie.

|||
|-|-|
|operator godzin "" h (bez znaku long long Val)|Określa godziny jako wartość całkowitą.|
|\<double czasu trwania, współczynnik \<3600 > > operator "" h (long double Val)|Określa godziny jako wartość zmiennoprzecinkową.|
|minuty (operator "min") (bez znaku long long Val)|Określa liczbę minut jako wartość całkowitą.|
|\<double czasu trwania, współczynnik \<60 > > (operator "" min) (long double Val)|Określa liczbę minut jako wartość zmiennoprzecinkową.|
|operator sekund "" s (bez znaku long long Val)|Określa liczbę minut jako wartość całkowitą.|
|czas trwania \<double operatora > "" s (long double Val)|Określa liczbę sekund jako wartość zmiennoprzecinkową.|
|milisekundy operatora "" MS (bez znaku long long Val)|Określa milisekundy jako wartość całkowitą.|
|czas trwania \<double, operator Milli > "" MS (long double Val)|Określa milisekundy jako wartość zmiennoprzecinkową.|
|operator mikrosekund "" US (bez znaku long long Val)|Określa mikrosekundy jako wartość całkowitą.|
|czas trwania \<double, mikro > operator "" US (long double Val)|Określa mikrosekund jako wartość zmiennoprzecinkową.|
|operator nanosekund "" NS (bez znaku long long Val)|Określa liczbę nanosekund jako wartość całkowitą.|
|czas trwania \<double, operator nano > "" NS (long double Val)|Określa liczbę nanosekund jako wartość zmiennoprzecinkową.|

W poniższych przykładach pokazano, jak używać literałów Chrono.

```cpp
constexpr auto day = 24h;
constexpr auto week = 24h* 7;
constexpr auto my_duration_unit = 108ms;
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
