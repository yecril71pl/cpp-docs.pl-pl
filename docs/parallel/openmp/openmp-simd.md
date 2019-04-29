---
title: Rozszerzenia SIMD
ms.date: 03/20/2019
helpviewer_keywords:
- SIMD
- OpenMP in Visual C++, new features
- explicit parallelization, new features
ms.openlocfilehash: 52402aa553c6d68d3073aba26ecac7b784522ee9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363274"
---
# <a name="simd-extension"></a>Rozszerzenia SIMD

Wizualne C++ jednak 2019 usługi Visual Studio oferuje teraz również funkcje SIMD obsługuje obecnie standard OpenMP 2.0.

> [!NOTE]
> Aby użyć SIMD, skompilować z `-openmp:experimental` przełącznika, który umożliwia dodatkowe funkcje OpenMP nie jest dostępna, korzystając z `-openmp` przełącznika.
>
> `-openmp:experimental` Obejmuje przełącznika `-openmp`, co oznacza wszystkie funkcje OpenMP 2.0 są uwzględnione w jego użycia.

Aby uzyskać więcej informacji, zobacz [rozszerzenia SIMD C++ OpenMP w programie Visual Studio](https://devblogs.microsoft.com/cppblog/simd-extension-to-c-openmp-in-visual-studio/).

## <a name="openmp-simd-in-visual-c"></a>OpenMP SIMD w wizualizacjiC++

OpenMP SIMD wprowadzone w warstwie standardowa 4.0 OpenMP cele wprowadzania pętli przyjaznego dla wektora. Za pomocą `simd` dyrektywy przed pętli, kompilator można zignorować wektor zależności, należy pętli jako wektor przyjaznego możliwie, a przestrzegają zamiar użytkowników mają wiele iteracji pętli wykonywane jednocześnie.

```c
    #pragma omp simd
    for (i = 0; i < count; i++)
    {
        a[i] = a[i-1] + 1;
        b[i] = *c + 1;
        bar(i);
    }
```

Visual C++ zawiera podobne-OpenMP pętli pragm, takich jak `#pragma vector` i `#pragma ivdep`, jednak OpenMP SIMD, kompilator wykonać więcej informacji, takich jak:

- Zawsze dozwolona ignorowanie obecne zależności wektora.
- `/fp:fast` jest włączone w ramach pętli.
- Zewnętrzne pętli i pętli za pomocą wywołania funkcji są przyjazne wektora.
- Pętle zagnieżdżone może być scalone w jeden pętli i wprowadzone przyjaznego dla wektora.
- Przyspieszanie hybrydowego za pomocą `#pragma omp for simd` umożliwiające gruboziarnistych wektorów wielowątkowości i precyzyjny.  

Dla pętli przyjaznego dla wektor kompilator pozostaje dyskretnej, chyba że używasz przełącznika dzienników pomocy technicznej wektora:

```cmd
    cl -O2 -openmp:experimental -Qvec-report:2 mycode.cpp
```

```Output
    mycode.cpp(84) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(90) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(96) : info C5001: Omp simd loop vectorized
```

Dla pętli innych niż przyjazne wektora w kompilator generuje każdy komunikat:

```cmd
    cl -O2 -openmp:experimental mycode.cpp
```

```Output
    mycode.cpp(84) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(90) : info C5002: Omp simd loop not vectorized due to reason '1200'
```

### <a name="clauses"></a>Klauzule

Dyrektywy OpenMP SIMD możesz skorzystać z następujących klauzul, aby poprawić obsługę wektora:

|— Dyrektywa|Opis|
|---|---|
|`simdlen(length)`|Określ liczbę tory wektora.|
|`safelen(length)`|Określ odległość zależności wektora.|
|`linear(list[ : linear-step]`)|Liniowy mapowanie z pętli, zmienna indukowana do tablicy subskrypcji.|
|`aligned(list[ : alignment])`|Wyrównanie danych.|
|`private(list)`|Określ prywatyzacji danych.|
|`lastprivate(list)`|Określ prywatyzacji data końcowa wartość z ostatniej iteracji.|
|`reduction(reduction-identifier:list)`|Określ dostosowane redukcji operacji.|
|`collapse(n)`|Łączącego zagnieżdżonych pętli.|

> [!NOTE]
> Klauzule SIMD obowiązywać inne niż są analizowane i ignorowane przez kompilator z ostrzeżeniem.
>
> Na przykład należy użyć następujących problemów kod ostrzeżenia:
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
  
Dyrektywy OpenMP SIMD umożliwia użytkownikom dyktowania kompilatora upewnij pętli wektor przyjaznego dla. Przez dodawanie adnotacji do pętli za pomocą dyrektywy OpenMP SIMD, użytkownicy mają być wiele iteracji pętli wykonywane jednocześnie.

Na przykład następującą pętlę jest oznaczona za pomocą dyrektywy OpenMP SIMD. Istnieje nie doskonałe równoległości między iteracji pętli, ponieważ istnieje zależność z poprzednimi wersjami z [i] do [i-1], ale z powodu dyrektywy SIMD, którą kompilator nadal może pakietu kolejne iteracje pierwsza instrukcja w jedną wektora, a następnie uruchom ich równolegle.

```c
    #pragma omp simd
    for (i = 0; i < count; i++)
    {
        a[i] = a[i-1] + 1;
        b[i] = *c + 1;
        bar(i);
    }
```

Dlatego jest następującą postać wektor przekształcone w pętli **prawne** ponieważ kompilator zachowuje sekwencyjne zachowanie oryginalnej iteracji pętli. Innymi słowy `a[i]` jest wykonywany po `a[-1]`, `b[i]` po `a[i]` i wywołania `bar` się stanie w ostatnich.

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

Ma ona **nie prawne** przenieść odwołanie do pamięci `*c` wyjścia z pętli, jeśli alias może się za pomocą `a[i]` lub `b[i]`. Również nie jest prawnych, aby zmienić kolejność instrukcji w jednej iteracji oryginalnej, jeśli przerywa zależności, sekwencyjny. Na przykład następującą pętlę przekształcone nie prawne:

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

## <a name="see-also"></a>Zobacz także

[/openmp (Włącz obsługę OpenMP 2.0)](../../build/reference/openmp-enable-openmp-2-0-support.md)<br/>
