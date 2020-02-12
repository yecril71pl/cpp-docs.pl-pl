---
title: 'Porady: pisanie pętli parallel_for'
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel_for loop [Concurrency Runtime]
- parallel_for function, example
ms.assetid: adb4d64e-5514-4b70-8dcb-b9210e6b5a1c
ms.openlocfilehash: 5903114a12de46dc06929c83e9995b39d0136810
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141858"
---
# <a name="how-to-write-a-parallel_for-loop"></a>Porady: pisanie pętli parallel_for

Ten przykład ilustruje sposób użycia [współbieżności::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) do obliczenia iloczynu dwóch macierzy.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje funkcję `matrix_multiply`, która oblicza iloczyn dwóch macierzy kwadratowych.

[!code-cpp[concrt-parallel-matrix-multiply#1](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_1.cpp)]

## <a name="example"></a>Przykład

Poniższy przykład pokazuje funkcję `parallel_matrix_multiply`, która używa algorytmu `parallel_for` do równoległego wykonywania pętli zewnętrznej.

[!code-cpp[concrt-parallel-matrix-multiply#2](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_2.cpp)]

Ten przykład parallelizes pętlę zewnętrzną tylko, ponieważ wykonuje wystarczającą ilość pracy, aby korzystać z obciążania przetwarzania równoległego. Jeśli zrównoleglanie pętlę wewnętrzną, nie otrzymasz wydajności, ponieważ niewielka ilość pracy wykonywanej przez pętlę wewnętrzną nie przeniesie obciążenia do przetwarzania równoległego. W związku z tym przekształcają pętlę zewnętrzną to najlepszy sposób, aby zmaksymalizować zalety współbieżności w większości systemów.

## <a name="example"></a>Przykład

Poniższy bardziej kompletny przykład porównuje wydajność funkcji `matrix_multiply` w porównaniu z funkcją `parallel_matrix_multiply`.

[!code-cpp[concrt-parallel-matrix-multiply#3](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_3.cpp)]

Następujące przykładowe dane wyjściowe dotyczą komputera, który ma cztery procesory.

```Output
serial: 3853
parallel: 1311
```

## <a name="compiling-the-code"></a>Kompilowanie kodu

Aby skompilować kod, skopiuj go, a następnie wklej w projekcie programu Visual Studio lub wklej go w pliku o nazwie `parallel-matrix-multiply.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

> **CL. exe/EHsc Parallel-Matrix-Multiply. cpp**

## <a name="see-also"></a>Zobacz też

[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)<br/>
[Funkcja parallel_for](reference/concurrency-namespace-functions.md#parallel_for)
