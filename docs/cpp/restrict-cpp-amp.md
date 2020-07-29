---
title: ograniczenie (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- cpu_CPP
- amp_CPP
helpviewer_keywords:
- restrict clause (C++ AMP)
ms.assetid: 07d3291f-7edf-456b-8828-283ac8673661
ms.openlocfilehash: 31db9e8c6f18879e65596593c10a8b3413c5cea9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213271"
---
# <a name="restrict-c-amp"></a>ograniczenie (C++ AMP)

Specyfikator ograniczenia może być stosowany do funkcji i deklaracji lambda. Wymusza on ograniczenia dotyczące kodu w funkcji i zachowania funkcji w zastosowaniach, które korzystają ze środowiska uruchomieniowego C++ Accelerated Massive Parallelism (C++ AMP).

> [!NOTE]
> Aby uzyskać informacje na temat **`restrict`** słowa kluczowego, które jest częścią **`__declspec`** atrybutów klasy magazynu, zobacz [ograniczanie](../cpp/restrict.md).

**`restrict`** Klauzula przyjmuje następujące formy:

|Klauzula|Opis|
|------------|-----------------|
|`restrict(cpu)`|Funkcja może używać w pełni języka C++. Tylko inne funkcje, które są zadeklarowane za pomocą funkcji restrict(cpu) mogą wywołać tę funkcję.|
|`restrict(amp)`|Funkcja może używać tylko podzbioru języka C++, który może być przyspieszony przez C++ AMP.|
|Sekwencja `restrict(cpu)` i `restrict(amp)`.|Funkcja musi stosować się do ograniczeń zarówno `restrict(cpu)`, jak i `restrict(amp)`. Funkcja może być wywołana przez funkcje, które są zadeklarowane przy użyciu `restrict(cpu)`, `restrict(amp)`, `restrict(cpu, amp)` lub `restrict(amp, cpu)`.<br /><br /> Postać `restrict(A) restrict(B)` może być zapisana jako `restrict(A,B)`.|

## <a name="remarks"></a>Uwagi

**`restrict`** Słowo kluczowe jest kontekstowym słowem kluczowym. Specyfikatory ograniczeń `cpu` i `amp` nie są słowami zarezerwowanymi. Lista specyfikatorów nie jest rozszerzalna. Funkcja, która nie ma klauzuli, **`restrict`** jest taka sama jak funkcja, która ma `restrict(cpu)` klauzulę.

Funkcja z klauzulą `restrict(amp)` ma następujące ograniczenia:

- Funkcja może wywołać tylko funkcje z klauzulą `restrict(amp)`.

- Funkcja musi być możliwa do wbudowania.

- Funkcja może deklarować tylko **`int`** zmienne, **`unsigned int`** , **`float`** , i **`double`** oraz klasy i struktury, które zawierają tylko te typy. **`bool`** jest również dozwolone, ale musi być wyrównania 4-bajtowe, jeśli jest używany w typie złożonym.

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

  - **`goto`** zatwierdzeni.

  - Instrukcje oznaczone.

  - **`try`**, **`catch`** , lub **`throw`** instrukcji.

  - Zmienne globalne.

  - Zmienne statyczne. Zamiast tego użyj [słowa kluczowego tile_static](../cpp/tile-static-keyword.md) .

  - **`dynamic_cast`** rzutowania.

  - **`typeid`** Operator.

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

## <a name="see-also"></a>Zobacz także

[C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)
