---
title: ograniczenie (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- cpu_CPP
- amp_CPP
helpviewer_keywords:
- restrict clause (C++ AMP)
ms.assetid: 07d3291f-7edf-456b-8828-283ac8673661
ms.openlocfilehash: b3464b758c6b66cdbd5015ee4b7c9d11eb2209dd
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404941"
---
# <a name="restrict-c-amp"></a>ograniczenie (C++ AMP)

Specyfikator ograniczenia może być stosowany do funkcji i deklaracji lambda. Wymusza on ograniczenia dotyczące kodu w funkcji i zachowania funkcji w zastosowaniach, które korzystają ze środowiska uruchomieniowego C++ Accelerated Massive Parallelism (C++ AMP).

> [!NOTE]
> Aby uzyskać informacje na temat **ograniczenia** słowa kluczowego, które jest częścią atrybutów klasy magazynu **__declspec** , zobacz [ograniczanie](../cpp/restrict.md).

Klauzula **ograniczenia** przyjmuje następujące formy:

|Klauzula|Opis|
|------------|-----------------|
|`restrict(cpu)`|Funkcja może używać w pełni języka C++. Tylko inne funkcje, które są zadeklarowane za pomocą funkcji restrict(cpu) mogą wywołać tę funkcję.|
|`restrict(amp)`|Funkcja może używać tylko podzbioru języka C++, który może być przyspieszony przez C++ AMP.|
|Sekwencja `restrict(cpu)` i `restrict(amp)`.|Funkcja musi stosować się do ograniczeń zarówno `restrict(cpu)`, jak i `restrict(amp)`. Funkcja może być wywołana przez funkcje, które są zadeklarowane przy użyciu `restrict(cpu)`, `restrict(amp)`, `restrict(cpu, amp)` lub `restrict(amp, cpu)`.<br /><br /> Postać `restrict(A) restrict(B)` może być zapisana jako `restrict(A,B)`.|

## <a name="remarks"></a>Uwagi

Słowo kluczowe **ograniczenia** jest kontekstowym słowem kluczowym. Specyfikatory ograniczeń `cpu` i `amp` nie są słowami zarezerwowanymi. Lista specyfikatorów nie jest rozszerzalna. Funkcja, która nie ma klauzuli **ograniczenia** , jest taka sama jak funkcja, która ma `restrict(cpu)` klauzulę.

Funkcja z klauzulą `restrict(amp)` ma następujące ograniczenia:

- Funkcja może wywołać tylko funkcje z klauzulą `restrict(amp)`.

- Funkcja musi być możliwa do wbudowania.

- Funkcja może deklarować tylko zmienne **int**, **unsigned int**, **float**i **Double** oraz klasy i struktury, które zawierają tylko te typy. wartość **logiczna** jest również dozwolona, ale musi być wyrównania 4-bajtowego, jeśli jest używana w typie złożonym.

- Funkcje lambda nie mogą przechwytywać poprzez odwołanie i nie mogą przechwytywać wskaźników.

- Odwołania i wskaźniki pojedynczego pośrednictwa są obsługiwane tylko jako zmienne lokalne, argumenty funkcji i typy zwracane.

- Nie są dozwolone:

  - Rekursja.

  - Zmienne zadeklarowane za pomocą słowa kluczowego [volatile](../cpp/volatile-cpp.md) .

  - Funkcje wirtualne.

  - Wskaźniki do funkcji.

  - Wskaźniki do funkcji członkowskich.

  - Wskaźniki w strukturach.

  - Wskaźniki do wskaźników.

  - instrukcji **goto** .

  - Instrukcje oznaczone.

  - instrukcje **try**, **catch**i **throw** .

  - Zmienne globalne.

  - Zmienne statyczne. Zamiast tego użyj [słowa kluczowego tile_static](../cpp/tile-static-keyword.md) .

  - **dynamic_cast** casts.

  - Operator **typeid** .

  - Deklaracje asm.

  - Elementy vararg.

Omówienie ograniczeń funkcji znajduje się w temacie [ograniczenia (amp)](/archive/blogs/nativeconcurrency/restrictamp-restrictions-part-0-of-n-introduction).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać `restrict(amp)` klauzuli.

```cpp
void functionAmp() restrict(amp) {}
void functionNonAmp() {}

void callFunctions() restrict(amp)
{
    // int is allowed.
    int x;
    // long long int is not allowed in an amp-restricted function. This generates a compiler error.
    // long long int y;

    // Calling an amp-restricted function is allowed.
    functionAmp();

    // Calling a non-amp-restricted function is not allowed.
    // functionNonAmp();
}
```

## <a name="see-also"></a>Zobacz też

[C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)
