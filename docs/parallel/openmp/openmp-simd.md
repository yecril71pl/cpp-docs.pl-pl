---
title: Rozszerzenie SIMD
ms.date: 03/20/2019
helpviewer_keywords:
- SIMD
- OpenMP in Visual C++, new features
- explicit parallelization, new features
ms.openlocfilehash: 0a7f1142a3a432628795341f4885b76a5c144990
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366453"
---
# <a name="simd-extension"></a>Rozszerzenie SIMD

Visual C++ obsługuje obecnie standard OpenMP 2.0, jednak visual studio 2019 oferuje teraz również funkcje SIMD.

> [!NOTE]
> Aby użyć karty SIMD, `-openmp:experimental` skompiluj za pomocą przełącznika, który włącza dodatkowe funkcje OpenMP niedostępne podczas korzystania z przełącznika. `-openmp`
>
> `-openmp:experimental` Podporządkowanie `-openmp`przełącznika, co oznacza, że wszystkie funkcje OpenMP 2.0 są uwzględnione w jego użyciu.

Aby uzyskać więcej informacji, zobacz [Rozszerzenie SIMD do programu OpenMP języka C++ w programie Visual Studio](https://devblogs.microsoft.com/cppblog/simd-extension-to-c-openmp-in-visual-studio/).

## <a name="openmp-simd-in-visual-c"></a>OpenMP SIMD w programie Visual C++

OpenMP SIMD, wprowadzony w standardzie OpenMP 4.0, jest przeznaczony do tworzenia pętli przyjaznych dla wektorów. Za pomocą `simd` dyrektywy przed pętli kompilator można zignorować zależności wektora, aby pętla jako przyjazne dla wektora, jak to możliwe i szanować intencji użytkowników, aby mieć wiele iteracji pętli wykonywane jednocześnie.

```c
    #pragma omp simd
    for (i = 0; i < count; i++)
    {
        a[i] = a[i-1] + 1;
        b[i] = *c + 1;
        bar(i);
    }
```

Visual C++ zapewnia podobne pragmy pętli `#pragma vector` `#pragma ivdep`non-OpenMP, takie jak i , jednak z OpenMP SIMD, kompilator może zrobić więcej, jak:

- Zawsze wolno ignorować obecne zależności wektora.
- `/fp:fast`jest włączona w pętli.
- Zewnętrzne pętle i pętle z wywołaniami funkcji są przyjazne dla wektora.
- Zagnieżdżone pętle mogą być zleczone w jedną pętlę i przyjazne dla wektora.
- Przyspieszenie hybrydowe w `#pragma omp for simd` celu umożliwienia gruboziarnistych wektorów wielowątkowych i drobnoziarnistych.  

W przypadku pętli przyjaznych dla wektora kompilator pozostaje cichy, chyba że używasz przełącznika dziennika obsługi wektorowej:

```cmd
    cl -O2 -openmp:experimental -Qvec-report:2 mycode.cpp
```

```Output
    mycode.cpp(84) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(90) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(96) : info C5001: Omp simd loop vectorized
```

W przypadku pętli nieprzychylonych kompilator wydaje każdy komunikat:

```cmd
    cl -O2 -openmp:experimental mycode.cpp
```

```Output
    mycode.cpp(84) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(90) : info C5002: Omp simd loop not vectorized due to reason '1200'
```

### <a name="clauses"></a>Klauzule

Dyrektywa OpenMP SIMD może również przyjąć następujące klauzule w celu zwiększenia obsługi wektorowej:

|Dyrektywy|Opis|
|---|---|
|`simdlen(length)`|Określ liczbę pasów wektorowych.|
|`safelen(length)`|Określ odległość zależności wektorowej.|
|`linear(list[ : linear-step]`)|Mapowanie liniowe od zmiennej indukcyjnej pętli do subskrypcji tablicy.|
|`aligned(list[ : alignment])`|Wyrównanie danych.|
|`private(list)`|Określ prywatyzację danych.|
|`lastprivate(list)`|Określ prywatyzację danych z wartością końcową z ostatniej iteracji.|
|`reduction(reduction-identifier:list)`|Określ dostosowane operacje redukcji.|
|`collapse(n)`|Scalanie gniazda pętli.|

> [!NOTE]
> Nieefektywne klauzule SIMD są analizowane i ignorowane przez kompilator z ostrzeżeniem.
>
> Na przykład użycie następującego kodu wydaje ostrzeżenie:
>
> ```c
>    #pragma omp simd simdlen(8)
>    for (i = 0; i < count; i++)
>    {
>        a[i] = a[i-1] + 1;
>        b[i] = *c + 1;
>        bar(i);
>    }
> ```
>
> ```Output
>    warning C4849: OpenMP 'simdlen' clause ignored in 'simd' directive
> ```

### <a name="example"></a>Przykład
  
Dyrektywa OpenMP SIMD zapewnia użytkownikom sposób dyktowania kompilatora pętli wektora przyjazne. Dzięki adnotacji pętli z dyrektywą OpenMP SIMD użytkownicy zamierzają mieć wiele iteracji pętli wykonywanych jednocześnie.

Na przykład następująca pętla jest adnotacjami z dyrektywą OpenMP SIMD. Nie ma idealnego równoległości między iteracjami pętli, ponieważ istnieje zależność wsteczna od [i] do[i-1], ale ze względu na dyrektywę SIMD kompilator nadal może pakować kolejne iteracje pierwszej instrukcji do jednej instrukcji wektorowej i uruchamiać je równolegle.

```c
    #pragma omp simd
    for (i = 0; i < count; i++)
    {
        a[i] = a[i-1] + 1;
        b[i] = *c + 1;
        bar(i);
    }
```

W związku z tym następujące przekształcone wektorformy pętli jest **legalne,** ponieważ kompilator zachowuje sekwencyjne zachowanie każdej oryginalnej iteracji pętli. Innymi słowy, `a[i]` jest `a[-1]`wykonywany `b[i]` po `a[i]` , jest `bar` po i wywołanie dzieje się ostatnio.

```c
    for (i = 0; i < count; i+=4)
    {
        a[i:i+3] = a[i-1:i+2] + 1;
        b[i:i+3] = *c + 1;
        bar(i);
        bar(i+1);
        bar(i+2);
        bar(i+3);
    }
```

Nie jest **legalne,** aby `*c` przenieść odwołanie do pamięci z `a[i]` `b[i]`pętli, jeśli może alias z lub . Nie jest również legalne, aby zamieścić kolejność instrukcji wewnątrz jednej oryginalnej iteracji, jeśli przerywa zależność sekwencyjną. Na przykład następująca przekształcona pętla nie jest legalna:

```c
    c = b;
    t = *c;
    for (i = 0; i < count; i+=4)
    {
        a[i:i+3] = a[i-1:i+2] + 1;
        bar(i);            // illegal to reorder if bar[i] depends on b[i]
        b[i:i+3] = t + 1;  // illegal to move *c out of the loop
        bar(i+1);
        bar(i+2);
        bar(i+3);
    }
```

## <a name="see-also"></a>Zobacz też

[/openmp (Włącz obsługę OpenMP 2.0)](../../build/reference/openmp-enable-openmp-2-0-support.md)<br/>
