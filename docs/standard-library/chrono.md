---
title: '&lt;chrono&gt;'
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
ms.openlocfilehash: 44620b6ea6c970027a8e9a023c0972c6dec43ee0
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220247"
---
# <a name="ltchronogt"></a>&lt;chrono&gt;

Dołączyć standardowy nagłówek \<chrono > do zdefiniowania klasy i funkcje, które reprezentują i manipulować czasów i czasie czasu.

Począwszy od programu Visual Studio 2015, implementacja `steady_clock` został zmieniony, aby spełniać wymagania C++ Standard opanowanie i monotonicity. `steady_clock` teraz jest oparty na QueryPerformanceCounter() i `high_resolution_clock` jest teraz element typedef dla `steady_clock`. W rezultacie w programie Microsoft C++ kompilatora `steady_clock::time_point` jest teraz element typedef dla `chrono::time_point<steady_clock>`; jednak nie jest w przypadku innych implementacji.

## <a name="syntax"></a>Składnia

```cpp
#include <chrono>
```

### <a name="classes"></a>Klasy

|Nazwa|Opis|
|----------|-----------------|
|[duration, klasa](../standard-library/duration-class.md)|Opisuje typ, który zawiera interwał czasu.|
|[time_point, klasa](../standard-library/time-point-class.md)|Opisuje typ, który reprezentuje punkt w czasie.|

### <a name="structs"></a>Struktury

|Nazwa|Opis|
|----------|-----------------|
|[common_type, struktura](../standard-library/common-type-structure.md)|Opisuje specjalizacje szablonu klasy [common_type](../standard-library/common-type-class.md) dla instancji `duration` i `time_point`.|
|[duration_values, struktura](../standard-library/duration-values-structure.md)|Zawiera określone wartości dla `duration` parametru szablonu `Rep`.|
|[steady_clock, struktura](../standard-library/steady-clock-struct.md)|Reprezentuje `steady` zegara.|
|[system_clock, struktura](../standard-library/system-clock-structure.md)|Reprezentuje *typ zegara* jest oparty na zegarze w czasie rzeczywistym systemu.|
|[treat_as_floating_point, struktura](../standard-library/treat-as-floating-point-structure.md)|Określa, czy typ może być traktowana jako typ zmiennoprzecinkowy.|

### <a name="functions"></a>Funkcje

|Nazwa|Opis|
|----------|-----------------|
|[duration_cast](../standard-library/chrono-functions.md#duration_cast)|Rzutowania `duration` obiektu określonego typu.|
|[time_point_cast](../standard-library/chrono-functions.md#time_point_cast)|Rzutowania `time_point` obiektu określonego typu.|

### <a name="operators"></a>Operatory

|Nazwa|Opis|
|----------|-----------------|
|[operator-](../standard-library/chrono-operators.md#operator-)|Operator odejmowania lub negacji `duration` i `time_point` obiektów.|
|[operator!=](../standard-library/chrono-operators.md#op_neq)|Operator nierówności, który jest używany z `duration` lub `time_point` obiektów.|
|[Operator modulo](../standard-library/chrono-operators.md#op_modulo)|Operator modulo operacji na `duration` obiektów.|
|[operator*](../standard-library/chrono-operators.md#op_star)|Operator mnożenia dla `duration` obiektów.|
|[operator/](../standard-library/chrono-operators.md#op_div)|Operator dzielenia dla `duration` obiektów.|
|[operator +](../standard-library/chrono-operators.md#op_add)|Dodaje `duration` i `time_point` obiektów.|
|[Operator&lt;](../standard-library/chrono-operators.md#op_lt)|Określa, czy jeden `duration` lub `time_point` obiekt jest mniejszy niż inny `duration` lub `time_point` obiektu.|
|[Operator&lt;=](../standard-library/chrono-operators.md#op_lt_eq)|Określa, czy jeden `duration` lub `time_point` obiekt jest mniejszy niż lub równy innemu `duration` lub `time_point` obiektu.|
|[operator==](../standard-library/chrono-operators.md#op_eq_eq)|Określa, czy dwa `duration` obiekty reprezentują przedziały czasowe, które mają taką samą długość, czy dwa `time_point` obiekty reprezentują tego samego punktu w czasie.|
|[Operator&gt;](../standard-library/chrono-operators.md#op_gt)|Określa, czy jeden `duration` lub `time_point` obiekt jest większy niż inny `duration` lub `time_point` obiektu.|
|[Operator&gt;=](../standard-library/chrono-operators.md#op_gt_eq)|Określa, czy jeden `duration` lub `time_point` obiekt jest większy niż lub równy innemu `duration` lub `time_point` obiektu.|

### <a name="predefined-duration-types"></a>Czas trwania wstępnie zdefiniowanych typów

Aby uzyskać więcej informacji na temat typów współczynnik, które są używane następujące definicje typów, zobacz [ \<współczynnik >](../standard-library/ratio.md).

|Element TypeDef|Opis|
|-------------|-----------------|
|`typedef duration<long long, nano> nanoseconds;`|Synonim dla `duration` typ, który ma okres znaczników nanosekundowych jeden.|
|`typedef duration<long long, micro> microseconds;`|Synonim dla `duration` typ, który ma okres znaczników jeden mikrosekund.|
|`typedef duration<long long, milli> milliseconds;`|Synonim dla `duration` typ, który ma okres znaczników jeden milisekund.|
|`typedef duration<long long> seconds;`|Synonim dla `duration` typ, który ma okresu taktu w jednej sekundy.|
|`typedef duration<int, ratio<60> > minutes;`|Synonim dla `duration` typ, który ma okresu taktu w jednej minuty.|
|`typedef duration<int, ratio<3600> > hours;`|Synonim dla `duration` typ, który ma okresu taktu w jednej godziny.|

### <a name="literals"></a>Literały

**(C ++ 11)**  \<Chrono > nagłówka definiuje następujące [literały definiowane przez użytkownika](../cpp/user-defined-literals-cpp.md) umożliwia większą wygodę, bezpieczeństwo typów i łatwości utrzymania kodu. Literały te są definiowane w `literals::chrono_literals` wbudowanego w przestrzeni nazw i są zakresu, kiedy std::chrono znajduje się w zakresie.

|literał|Opis|
|-------------|-----------------|
|chrono::hours operator "" h (unsigned long long Val)|Określa godziny jako wartość całkowitą.|
|chrono::duration\<double, współczynnik\<3600 >> operator "" h (Val typu long double)|Określa godziny jako wartość zmiennoprzecinkowa.|
|chrono::minutes (operator "" min) (unsigned long long Val)|Określa minuty jako wartość całkowitą.|
|chrono::duration\<double, współczynnik\<60 >> (operator "" min) (liczba typu double Val)|Określa minuty jako wartość zmiennoprzecinkowa.|
|chrono::seconds operator "" s (unsigned long long Val)|Określa minuty jako wartość całkowitą.|
|chrono::duration\<double > — operator "" s (Val typu long double)|Określa w sekundach, jako wartość zmiennoprzecinkowa.|
|chrono::milliseconds operator "" ms (unsigned long long Val)|Określa milisekund, jako wartość całkowitą.|
|chrono::duration\<milli Podwójna precyzja > — operator "" ms (Val typu long double)|Określa milisekund, jako wartość zmiennoprzecinkowa.|
|chrono::microseconds operator "" us (unsigned long long Val)|Określa mikrosekund jako wartość całkowitą.|
|chrono::duration\<micro Podwójna precyzja > — operator "" us (Val typu long double)|Określa mikrosekund jako wartość zmiennoprzecinkowa.|
|chrono::nanoseconds operator "" ns (unsigned long long Val)|Określa nanosekundach jako wartość całkowitą.|
|chrono::duration\<nano Podwójna precyzja > — operator "" ns (Val typu long double)|Określa nanosekundach jako wartość zmiennoprzecinkowa.|
|||

Poniższe przykłady pokazują, jak używać literały chrono.

```cpp
constexpr auto day = 24h;
constexpr auto week = 24h* 7;
constexpr auto my_duration_unit = 108ms;
```

## <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
