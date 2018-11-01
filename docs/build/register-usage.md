---
title: Użycie metody Register
ms.date: 11/04/2016
ms.assetid: ce58e2cf-afd3-4068-980e-28a209298265
ms.openlocfilehash: fa04318ad4af298f300fbbbad8c01d0df9500ec7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629986"
---
# <a name="register-usage"></a>Użycie metody Register

X64 architektury stosowany do 16 rejestrów ogólnego przeznaczenia (zwany dalej rejestruje liczby całkowitej), a także 16 XMM/YMM rejestruje dostępny do użytku zmiennoprzecinkowych. Volatile rejestrów są pliki tymczasowe rejestrów domniemania przez obiekt wywołujący, które mają zostać zniszczone na wywołanie. Nieulotnej rejestrów są wymagane do zachowują swoje wartości w wywołaniu funkcji i musi zostać zapisany przez obiekt wywoływany, jeśli używany.

## <a name="register-volatility-and-preservation"></a>Zarejestruj zmienność i konserwacji

W poniższej tabeli opisano, jak każdy rejestr jest używany dla wywołań funkcji:

||||
|-|-|-|
|Rejestruj|Stan|Zastosowanie|
|RAX|Volatile|Zwracana wartość rejestru|
|RCX|Volatile|Pierwszy argument liczby całkowitej|
|RDX|Volatile|Drugi argument liczby całkowitej|
|R8|Volatile|Trzeci argument liczby całkowitej|
|R9|Volatile|Czwarty argument liczby całkowitej|
|R10:R11|Volatile|Muszą być chronione, zgodnie z potrzebami przez obiekt wywołujący; używane w instrukcjach syscall/sysret|
|R12:R15|Nieulotnej|Muszą być chronione przez wywoływanego|
|RDI|Nieulotnej|Muszą być chronione przez wywoływanego|
|RSI|Nieulotnej|Muszą być chronione przez wywoływanego|
|RBX|Nieulotnej|Muszą być chronione przez wywoływanego|
|RBP|Nieulotnej|Może być używana jako wskaźnik ramki; muszą być chronione przez wywoływanego|
|RSP|Nieulotnej|Wskaźnik stosu|
|XMM0, Z YMM0|Volatile|Pierwszy argument FP; pierwszy argument typu wektor podczas `__vectorcall` jest używany|
|XMM1, YMM1|Volatile|Drugi argument FP; drugi argument Typ wektora podczas `__vectorcall` jest używany|
|XMM2, YMM2|Volatile|Trzeci argument FP; trzeci argument Typ wektora podczas `__vectorcall` jest używany|
|XMM3, YMM3|Volatile|Czwarty argument FP; czwarty argument Typ wektora podczas `__vectorcall` jest używany|
|XMM4, YMM4|Volatile|Muszą być chronione, zgodnie z potrzebami przez obiekt wywołujący; piąty argument Typ wektora podczas `__vectorcall` jest używany|
|XMM5, YMM5|Volatile|Muszą być chronione, zgodnie z potrzebami przez obiekt wywołujący; szósty argument Typ wektora podczas `__vectorcall` jest używany|
|XMM6:XMM15, YMM6:YMM15|Nieulotnej (XMM) Volatile (górnej połowie YMM)|Muszą zostać zachowane przez obiekt wywoływany. Musi zostać zachowane rejestrach YMM, zgodnie z potrzebami przez obiekt wywołujący.|

Zamykania funkcji, wejście funkcji do wywołania biblioteki wykonawczej C i wywołań systemu Windows, Flaga kierunku w Procesorze flags, rejestrze powinien zostać wyczyszczone.

## <a name="see-also"></a>Zobacz także

- [Konwencje kodowania x64](../build/x64-software-conventions.md)
- [__vectorcall](../cpp/vectorcall.md)
- [Flaga kierunku](../c-runtime-library/direction-flag.md)
