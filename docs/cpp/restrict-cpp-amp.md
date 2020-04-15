---
title: ograniczenie (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- cpu_CPP
- amp_CPP
helpviewer_keywords:
- restrict clause (C++ AMP)
ms.assetid: 07d3291f-7edf-456b-8828-283ac8673661
ms.openlocfilehash: 5a0011d11e4a59c9ca3a5e18f44d4cf831b21582
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366644"
---
# <a name="restrict-c-amp"></a>ograniczenie (C++ AMP)

Specyfikator ograniczenia może być stosowany do funkcji i deklaracji lambda. Wymusza on ograniczenia dotyczące kodu w funkcji i zachowania funkcji w zastosowaniach, które korzystają ze środowiska uruchomieniowego C++ Accelerated Massive Parallelism (C++ AMP).

> [!NOTE]
> Aby uzyskać informacje o słowa kluczowego **ogranicz,** które jest częścią **atrybutów __declspec** klasy magazynu, zobacz [ogranicz](../cpp/restrict.md).

Klauzula **restrict** przyjmuje następujące formy:

|Klauzula|Opis|
|------------|-----------------|
|`restrict(cpu)`|Funkcja może używać w pełni języka C++. Tylko inne funkcje, które są zadeklarowane za pomocą funkcji restrict(cpu) mogą wywołać tę funkcję.|
|`restrict(amp)`|Funkcja może używać tylko podzbioru języka C++, który może być przyspieszony przez C++ AMP.|
|Sekwencja `restrict(cpu)` i `restrict(amp)`.|Funkcja musi stosować się do ograniczeń zarówno `restrict(cpu)`, jak i `restrict(amp)`. Funkcja może być wywołana przez funkcje, które są zadeklarowane przy użyciu `restrict(cpu)`, `restrict(amp)`, `restrict(cpu, amp)` lub `restrict(amp, cpu)`.<br /><br /> Postać `restrict(A) restrict(B)` może być zapisana jako `restrict(A,B)`.|

## <a name="remarks"></a>Uwagi

Słowo kluczowe **Restrict** jest słowem kluczowym kontekstowym. Specyfikatory ograniczeń `cpu` i `amp` nie są słowami zarezerwowanymi. Lista specyfikatorów nie jest rozszerzalna. Funkcja, która nie ma **klauzuli restrict** jest taka `restrict(cpu)` sama jak funkcja, która ma klauzulę.

Funkcja z klauzulą `restrict(amp)` ma następujące ograniczenia:

- Funkcja może wywołać tylko funkcje z klauzulą `restrict(amp)`.

- Funkcja musi być możliwa do wbudowania.

- Funkcja może deklarować tylko **int,** **unsigned int**, **float**i **podwójne** zmienne oraz klasy i struktury, które zawierają tylko te typy. **bool** jest również dozwolone, ale musi być wyrównany 4-bajtowy, jeśli używasz go w typie związku.

- Funkcje lambda nie mogą przechwytywać poprzez odwołanie i nie mogą przechwytywać wskaźników.

- Odwołania i wskaźniki pojedynczego pośrednictwa są obsługiwane tylko jako zmienne lokalne, argumenty funkcji i typy zwracane.

- Nie są dozwolone:

  - Rekursja.

  - Zmienne zadeklarowane za pomocą słowa kluczowego [volatile.](../cpp/volatile-cpp.md)

  - Funkcje wirtualne.

  - Wskaźniki do funkcji.

  - Wskaźniki do funkcji członkowskich.

  - Wskaźniki w strukturach.

  - Wskaźniki do wskaźników.

  - oświadczenia **goto.**

  - Instrukcje oznaczone.

  - **try**, **catch**, lub **throw** instrukcji.

  - Zmienne globalne.

  - Zmienne statyczne. Zamiast [tego użyj tile_static słowa kluczowego.](../cpp/tile-static-keyword.md)

  - **dynamic_cast** odlewy.

  - Operator **typeid.**

  - Deklaracje asm.

  - Elementy vararg.

Aby zapoznać się z omówieniami ograniczeń funkcji, zobacz [ograniczanie ograniczeń .amp.](https://blogs.msdn.microsoft.com/nativeconcurrency/2011/12/19/restrictamp-restrictions-part-0-of-n-introduction/)

## <a name="example"></a>Przykład

W poniższym przykładzie `restrict(amp)`pokazano, jak używać klauzuli.

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
