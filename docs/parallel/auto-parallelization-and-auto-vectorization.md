---
title: Automatyczna paralelizacja i wektoryzacja
ms.date: 11/04/2016
ms.assetid: ec71583a-287b-4599-8767-1d255e080fe3
ms.openlocfilehash: 06ab255e7769bfa56d5a8d22cdbe19d415ce6b31
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618351"
---
# <a name="auto-parallelization-and-auto-vectorization"></a>Automatyczna paralelizacja i wektoryzacja

Auto-Parallelizer and Auto-Vectorizer są przeznaczone do zapewnienia wzrost wydajności automatyczne pętli w kodzie.

## <a name="auto-parallelizer"></a>Diagnostyka zrównoleglenia automatycznego

[/Qpar](../build/reference/qpar-auto-parallelizer.md) umożliwia przełącznika kompilatora *automatyczne przetwarzanie równoległe* pętli w kodzie. Po określeniu tej flagi bez zmieniania istniejącego kodu, kompilator oblicza kod, aby znaleźć pętli, które mogą skorzystać z przetwarzaniem równoległym. Ponieważ może odnaleźć pętli, które nie wykonują większość pracy i w związku z tym nie przynoszą korzyści, od przetwarzania równoległego, a ponieważ każdy niepotrzebne przetwarzania równoległego może stanowić zagrożenie podczas duplikowania puli wątków, dodatkowe synchronizacji lub innego przetwarzania, które mogą one spowolnić wydajność zamiast ulepszeń, kompilator jest Konserwatywny wyborze pętli, które go parallelizes. Na przykład rozważmy poniższy przykład, w którym górną granicę pętli nie jest znany w czasie kompilacji:

```cpp
void loop_test(int u) {
   for (int i=0; i<u; ++i)
      A[i] = B[i] * C[i];
}
```

Ponieważ `u` może być małej wartości, kompilator nie będzie automatycznie zrównoleglić pętlę. Jednak nadal może być ona zrównoleglona, ponieważ wiesz, że `u` będzie zawsze duże. Aby włączyć automatyczne przetwarzanie równoległe, określ [#pragma loop(hint_parallel(n))](../preprocessor/loop.md), gdzie `n` jest to liczba wątków do zrównoleglenia między. W poniższym przykładzie kompilator będzie próbował zrównoleglić pętlę w 8 wątków.

```cpp
void loop_test(int u) {
#pragma loop(hint_parallel(8))
   for (int i=0; i<u; ++i)
      A[i] = B[i] * C[i];
}
```

Podobnie jak w przypadku wszystkich [dyrektyw pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md), składni alternatywne pragma `__pragma(loop(hint_parallel(n)))` jest również obsługiwany.

Istnieją pewne pętli, które kompilator nie zrównoleglić nawet, jeśli chcesz, aby. Oto przykład:

```cpp
#pragma loop(hint_parallel(8))
for (int i=0; i<upper_bound(); ++i)
    A[i] = B[i] * C[i];
```

Funkcja `upper_bound()` mogą ulec zmianie, za każdym razem, gdy jest wywoływana. Ponieważ nie może być znane, górna granica, kompilator może emitować komunikat diagnostyczny, który wyjaśnia, dlaczego nie można zrównoleglić pętlę. Poniższy przykład pokazuje pętlę, która może być przetwarzane równolegle, pętlę, która nie może być przeprowadzana równolegle, składnia kompilatora, aby użyć w wierszu polecenia, a dane wyjściowe kompilatora dla każdej opcji wiersza polecenia:

```cpp
int A[1000];
void test() {
#pragma loop(hint_parallel(0))
    for (int i=0; i<1000; ++i) {
        A[i] = A[i] + 1;
    }

    for (int i=1000; i<2000; ++i) {
        A[i] = A[i] + 1;
    }
}
```

Kompilowanie za pomocą tego polecenia:

`cl d:\myproject\mylooptest.cpp /O2 /Qpar /Qpar-report:1`

daje następujące dane wyjściowe:

```Output
--- Analyzing function: void __cdecl test(void)
d:\myproject\mytest.cpp(4) : loop parallelized
```

Kompilowanie za pomocą tego polecenia:

`cl d:\myproject\mylooptest.cpp /O2 /Qpar /Qpar-report:2`

daje następujące dane wyjściowe:

```Output
--- Analyzing function: void __cdecl test(void)
d:\myproject\mytest.cpp(4) : loop parallelized
d:\myproject\mytest.cpp(4) : loop not parallelized due to reason '1008'
```

Należy zauważyć różnicę w danych wyjściowych między dwiema różnymi [/Qpar-report (poziom raportowania automatycznej Paralelizacji)](../build/reference/qpar-report-auto-parallelizer-reporting-level.md) opcje. `/Qpar-report:1` generuje komunikaty paralelizatora tylko dla pętli, które są pomyślnie zrównoleglona. `/Qpar-report:2` generuje komunikaty paralelizatora dla obu parallelizations pętli zakończone powodzeniem i niepowodzeniem.

Aby uzyskać więcej informacji na temat kodów przyczyn i komunikaty, zobacz [komunikaty Wektoryzatora i Paralelizatora](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).

## <a name="auto-vectorizer"></a>Auto-Vectorizer

Auto-Vectorizer analizuje pętli w kodzie i używa rejestrów wektorowych i instrukcje na komputerze docelowym można je wykonać, jeśli jest to możliwe. Może to poprawić wydajność kodu. Kompilator jest przeznaczony dla instrukcji SSE2, AVX i AVX2 w procesorach Intel lub AMD lub instrukcje NEON na procesorach ARM, zgodnie z opisem w [/arch](../build/reference/arch-minimum-cpu-architecture.md) przełącznika.

Auto-Vectorizer może wygenerować różne instrukcje, niż określa `/arch` przełącznika. Te instrukcje będą chronione przez sprawdzanie czasu wykonywania, aby upewnić się, że kod nadal działa poprawnie. Na przykład, gdy kompilujesz `/arch:SSE2`, może być emitowana instrukcji SSE4.2. Kontroli w czasie wykonywania sprawdza, czy SSE4.2 jest dostępny w procesor docelowy, a następnie przechodzi do wersji bez SSE4.2 pętli, jeśli procesora nie obsługuje tych instrukcji.

Domyślnie Auto-Vectorizer jest włączona. Jeśli chcesz porównać wydajność Twój kod w ramach wektoryzacji, możesz użyć [#pragma loop(no_vector)](../preprocessor/loop.md) wyłączyć wektoryzacji dowolnego danego pętli.

```cpp
#pragma loop(no_vector)
for (int i = 0; i < 1000; ++i)
   A[i] = B[i] + C[i];
```

Podobnie jak w przypadku wszystkich [dyrektyw pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md), składni alternatywne pragma `__pragma(loop(no_vector))` jest również obsługiwany.

Podobnie jak przy użyciu automatycznego Zrównoleglacza, można określić [/Qvec-report (poziom raportowania automatycznej Wektoryzacji)](../build/reference/qvec-report-auto-vectorizer-reporting-level.md) opcji wiersza polecenia, aby zgłosić albo pomyślnie wektoryzowana tylko pętli —`/Qvec-report:1`— lub oba pomyślnie i przekroczona wektoryzowana pętli —`/Qvec-report:2`).

Aby uzyskać więcej informacji na temat kodów przyczyn i komunikaty, zobacz [komunikaty Wektoryzatora i Paralelizatora](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).

Aby uzyskać przykład pokazujący, jak działa Diagnostyka wektoryzowania automatycznego w praktyce, zobacz [projektu Austin część 2 z 6: strony Curling](http://blogs.msdn.com/b/vcblog/archive/2012/09/27/10348494.aspx)

## <a name="see-also"></a>Zobacz też

[pętla](../preprocessor/loop.md)<br/>
[Programowanie równoległe w kodzie natywnym](http://go.microsoft.com/fwlink/p/?linkid=263662)<br/>
[/Qpar (Automatyczny paralelizator)](../build/reference/qpar-auto-parallelizer.md)<br/>
[/Qpar-raport (Poziom raportowania automatycznej paralelizacji)](../build/reference/qpar-report-auto-parallelizer-reporting-level.md)<br/>
[/Qvec-report (Poziom raportowania automatycznej wektoryzacji)](../build/reference/qvec-report-auto-vectorizer-reporting-level.md)<br/>
[Komunikaty wektoryzatora i paralelizatora](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)