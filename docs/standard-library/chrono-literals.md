---
title: literały chrono
ms.date: 11/04/2016
ms.assetid: 1a9e23b1-256f-4570-8226-5fa7364fb032
ms.openlocfilehash: d8416580df09a8a466678702cb20ba4ddf37eb28
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230159"
---
# <a name="chrono-literals"></a>literały chrono

(C++ 14) \<chrono>Nagłówek definiuje 12 [literałów zdefiniowanych przez użytkownika](../cpp/user-defined-literals-cpp.md) , aby ułatwić korzystanie z literałów, które reprezentują godziny, minuty, sekundy, milisekundy, mikrosekundy i nanosekund. Każdy literał zdefiniowany przez użytkownika ma całkowite i Przeciążenie zmiennoprzecinkowe. Literały są zdefiniowane w literałach:: chrono_literals wbudowanej przestrzeni nazw, która jest przenoszona do zakresu automatycznie, gdy std:: chrono znajduje się w zakresie.

## <a name="syntax"></a>Składnia

```cpp
inline namespace literals {
  inline namespace chrono_literals {
    // return integral hours
    constexpr chrono::hours operator"" h(unsigned long long Val);

    // return floating-point hours
    constexpr chrono::duration<double, ratio<3600>> operator"" h(long double Val);

    // return integral minutes
    constexpr chrono::minutes(operator"" min)(unsigned long long Val);

    // return floating-point minutes
    constexpr chrono::duration<double, ratio<60>>(operator"" min)(long double Val);

    // return integral seconds
    constexpr chrono::seconds operator"" s(unsigned long long Val);

    // return floating-point seconds
    constexpr chrono::duration<double> operator"" s(long double Val);

    // return integral milliseconds
    constexpr chrono::milliseconds operator"" ms(unsigned long long Val);

    // return floating-point milliseconds
    constexpr chrono::duration<double, milli> operator"" ms(long double Val);

    // return integral microseconds
    constexpr chrono::microseconds operator"" us(unsigned long long Val);

    // return floating-point microseconds
    inline constexpr chrono::duration<double, micro> operator"" us(long double Val);

    // return integral nanoseconds
    inline constexpr chrono::nanoseconds operator"" ns(unsigned long long Val);

    // return floating-point nanoseconds
    constexpr chrono::duration<double, nano> operator"" ns(long double Val);

  } // inline namespace chrono_literals
} // inline namespace literals
```

## <a name="return-value"></a>Wartość zwracana

Literały przyjmujące **`long long`** argument zwracają wartość lub odpowiedni typ. Literały przyjmujące argument zmiennoprzecinkowe zwracają [czas trwania](../standard-library/duration-class.md).

## <a name="example"></a>Przykład

W poniższych przykładach przedstawiono sposób użycia literałów Chrono.

```cpp
constexpr auto day = 24h;
constexpr auto week = 24h* 7;
constexpr auto my_duration_unit = 108ms;
```
