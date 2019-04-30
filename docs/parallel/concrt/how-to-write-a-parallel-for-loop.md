---
title: 'Instrukcje: Pisanie pętli parallel_for'
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel_for loop [Concurrency Runtime]
- parallel_for function, example
ms.assetid: adb4d64e-5514-4b70-8dcb-b9210e6b5a1c
ms.openlocfilehash: d6ac30a5de0ff45adad1064aeab708e6a84f5e9f
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346358"
---
# <a name="how-to-write-a-parallelfor-loop"></a>Instrukcje: Pisanie pętli parallel_for

W tym przykładzie przedstawiono sposób użycia [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) do Oblicz iloczyn dwóch macierzy.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono `matrix_multiply` funkcji, która oblicza iloczyn dwóch macierzy kwadratowych.

[!code-cpp[concrt-parallel-matrix-multiply#1](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_1.cpp)]

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono `parallel_matrix_multiply` funkcji, która używa `parallel_for` algorytm zewnętrzna pętla równolegle.

[!code-cpp[concrt-parallel-matrix-multiply#2](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_2.cpp)]

W tym przykładzie parallelizes zewnętrzna pętla tylko w przypadku, ponieważ wykonuje wystarczająco dużo pracy, aby korzystać z obciążenie do przetwarzania równoległego. Jeśli można zrównoleglić wewnętrzną pętlę, nie otrzymasz przyrost wydajności ponieważ niewielką ilość pracy, który wykonuje wewnętrzną pętlę nie przezwyciężyć obciążenie do przetwarzania równoległego. W związku z tym przekształcają zewnętrzna pętla tylko jest najlepszy sposób, aby zmaksymalizować korzyści współbieżności w większości systemów.

## <a name="example"></a>Przykład

Następujące bardziej rozbudowany przykład porównuje wydajność `matrix_multiply` funkcji w porównaniu z `parallel_matrix_multiply` funkcji.

[!code-cpp[concrt-parallel-matrix-multiply#3](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_3.cpp)]

Następujące przykładowe dane wyjściowe to dla komputera, który ma cztery procesory.

```Output
serial: 3853
parallel: 1311
```

## <a name="compiling-the-code"></a>Kompilowanie kodu

Aby skompilować ten kod, skopiuj go a następnie wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `parallel-matrix-multiply.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**Cl.exe/ehsc równoległych — macierz multiply.cpp**

## <a name="see-also"></a>Zobacz także

[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for Function](reference/concurrency-namespace-functions.md#parallel_for)
