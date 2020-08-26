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
ms.openlocfilehash: b74c25e9c26d5767426576633e0999ae3ca44954
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840651"
---
# <a name="ltchronogt"></a>&lt;Chrono&gt;

Dołącz standardowy nagłówek, \<chrono> Aby zdefiniować klasy i funkcje, które reprezentują i manipulowanie okresami czasowymi i czasem.

Począwszy od programu Visual Studio 2015, implementacja programu `steady_clock` została zmieniona tak, aby spełniała standardowe wymagania języka C++ dotyczące stałego i monotonicity. `steady_clock` jest teraz oparta na QueryPerformanceCounter () i `high_resolution_clock` jest teraz elementem TypeDef dla `steady_clock` . W związku z tym, w kompilatorze Microsoft C++ `steady_clock::time_point` jest teraz elementem TypeDef dla `chrono::time_point<steady_clock>` , jednak ta reguła nie jest konieczna dla innych implementacji.

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<chrono>

**Przestrzeń nazw:** std

## <a name="members"></a>Elementy członkowskie

### <a name="classes"></a>Klasy

|Nazwa|Opis|
|-|-|
|[Duration — Klasa](../standard-library/duration-class.md)|Opisuje typ, który przechowuje przedział czasu.|
|[Klasa time_point](../standard-library/time-point-class.md)|Opisuje typ, który reprezentuje punkt w czasie.|

### <a name="structs"></a>Struktury

|Nazwa|Opis|
|-|-|
|[common_type — Struktura](../standard-library/common-type-structure.md)|Opisuje specjalizacje [common_type](../standard-library/common-type-class.md) szablonu klasy dla wystąpień `duration` i `time_point` .|
|[duration_values — Struktura](../standard-library/duration-values-structure.md)|Zawiera określone wartości dla `duration` parametru szablonu `Rep` .|
|[Struktura high_resolution_clock](../standard-library/high-resolution-clock-struct.md)||
|[steady_clock — struktura](../standard-library/steady-clock-struct.md)|Przedstawia `steady` zegar.|
|[system_clock — Struktura](../standard-library/system-clock-structure.md)|Reprezentuje *Typ zegara* , który jest oparty na zegarze w czasie rzeczywistym systemu.|
|[treat_as_floating_point — Struktura](../standard-library/treat-as-floating-point-structure.md)|Określa, czy typ może być traktowany jako typ zmiennoprzecinkowy.|

### <a name="functions"></a>Functions

|Nazwa|Opis|
|-|-|
|[duration_cast](../standard-library/chrono-functions.md#duration_cast)|Rzutuje `duration` obiekt na określony typ.|
|[time_point_cast](../standard-library/chrono-functions.md#time_point_cast)|Rzutuje `time_point` obiekt na określony typ.|

### <a name="operators"></a>Operatory

|Nazwa|Opis|
|-|-|
|[zakład](../standard-library/chrono-operators.md#operator-)|Operator odejmowania lub negacji `duration` `time_point` obiektów i.|
|[operator! =](../standard-library/chrono-operators.md#op_neq)|Operator nierówności używany z `duration` lub `time_point` obiektami.|
|[modulo operatorów](../standard-library/chrono-operators.md#op_modulo)|Operator dla operacji modulo na `duration` obiektach.|
|[zakład](../standard-library/chrono-operators.md#op_star)|Operator mnożenia dla `duration` obiektów.|
|[zakład](../standard-library/chrono-operators.md#op_div)|Operator dzielenia dla `duration` obiektów.|
|[operator +](../standard-library/chrono-operators.md#op_add)|Dodaje `duration` `time_point` obiekty i.|
|[zakład&lt;](../standard-library/chrono-operators.md#op_lt)|Określa, czy jeden `duration` lub `time_point` obiekt jest mniejszy niż `duration` inny `time_point` obiekt lub.|
|[zakład&lt;=](../standard-library/chrono-operators.md#op_lt_eq)|Określa, czy jeden `duration` lub `time_point` obiekt jest mniejszy lub równy innemu `duration` lub `time_point` obiektowi.|
|[operator = =](../standard-library/chrono-operators.md#op_eq_eq)|Określa, czy dwa `duration` obiekty reprezentują przedziały czasu mające taką samą długość, czy dwa `time_point` obiekty reprezentują ten sam punkt w czasie.|
|[zakład&gt;](../standard-library/chrono-operators.md#op_gt)|Określa, czy jeden `duration` lub `time_point` obiekt jest większy niż `duration` inny `time_point` obiekt lub.|
|[zakład&gt;=](../standard-library/chrono-operators.md#op_gt_eq)|Określa, czy jeden `duration` lub `time_point` obiekt jest większy lub równy innemu `duration` lub `time_point` obiektowi.|

### <a name="typedefs-predefined-duration-types"></a>Typedefs (wstępnie zdefiniowane typy czasu trwania)

Aby uzyskać więcej informacji na temat typów współczynników, które są używane w następujących elementach typedef, zobacz [\<ratio>](../standard-library/ratio.md) .

|Nazwa|Opis|
|-|-|
|`typedef duration<long long, nano> nanoseconds;`|Synonim dla `duration` typu, który ma interwał o wartości 1 nanosekund.|
|`typedef duration<long long, micro> microseconds;`|Synonim dla `duration` typu, który ma wartość 1 mikrosekundowych.|
|`typedef duration<long long, milli> milliseconds;`|Synonim dla `duration` typu, który ma wartość 1 milisekund.|
|`typedef duration<long long> seconds;`|Synonim dla `duration` typu, który ma interwał o wartości 1 sekundy.|
|`typedef duration<int, ratio<60> > minutes;`|Synonim dla `duration` typu, który ma interwał o wartości 1 minuty.|
|`typedef duration<int, ratio<3600> > hours;`|Synonim dla `duration` typu, który ma godzinę 1 godziny.|

### <a name="literals"></a>Literały

**(C++ 11)** \<chrono> Nagłówek definiuje następujące [literały zdefiniowane przez użytkownika](../cpp/user-defined-literals-cpp.md) , których można użyć w celu zwiększenia wygody, bezpieczeństwa typów i utrzymania kodu. Te literały są zdefiniowane w `literals::chrono_literals` wbudowanej przestrzeni nazw i znajdują się w zakresie, gdy std:: chrono znajduje się w zakresie.

|Oświadczeń|Opis|
|-|-|
|`hours operator "" h(unsigned long long Val)`|Określa godziny jako wartość całkowitą.|
|`duration<double, ratio<3600> > operator "" h(long double Val)`|Określa godziny jako wartość zmiennoprzecinkową.|
|`minutes (operator "" min)(unsigned long long Val)`|Określa liczbę minut jako wartość całkowitą.|
|`duration<double, ratio<60> > (operator "" min)( long double Val)`|Określa liczbę minut jako wartość zmiennoprzecinkową.|
|`seconds operator "" s(unsigned long long Val)`|Określa liczbę minut jako wartość całkowitą.|
|`duration<double> operator "" s(long double Val)`|Określa liczbę sekund jako wartość zmiennoprzecinkową.|
|`milliseconds operator "" ms(unsigned long long Val)`|Określa milisekundy jako wartość całkowitą.|
|`duration<double, milli> operator "" ms(long double Val)`|Określa milisekundy jako wartość zmiennoprzecinkową.|
|`microseconds operator "" us(unsigned long long Val)`|Określa mikrosekundy jako wartość całkowitą.|
|`duration<double, micro> operator "" us(long double Val)`|Określa mikrosekund jako wartość zmiennoprzecinkową.|
|`nanoseconds operator "" ns(unsigned long long Val)`|Określa liczbę nanosekund jako wartość całkowitą.|
|`duration<double, nano> operator "" ns(long double Val)`|Określa liczbę nanosekund jako wartość zmiennoprzecinkową.|

W poniższych przykładach pokazano, jak używać literałów Chrono.

```cpp
constexpr auto day = 24h;
constexpr auto week = 24h* 7;
constexpr auto my_duration_unit = 108ms;
```

## <a name="see-also"></a>Zobacz też

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
