---
title: 'Porady: użyj anulowania, aby przerwać pętlę równoległą'
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel search algorithm [Concurrency Runtime]
- parallel search algorithm, writing [Concurrency Runtime]
ms.assetid: 421cd2de-f058-465f-b890-dd8fcc0df273
ms.openlocfilehash: 21907de6c5625f7774ae788cef0449ac49107e40
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142133"
---
# <a name="how-to-use-cancellation-to-break-from-a-parallel-loop"></a>Porady: użyj anulowania, aby przerwać pętlę równoległą

Ten przykład pokazuje, jak używać anulowania do implementowania podstawowego algorytmu wyszukiwania równoległego.

## <a name="example"></a>Przykład

Poniższy przykład używa anulowania, aby wyszukać element w tablicy. Funkcja `parallel_find_any` używa algorytmu [concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) oraz funkcji [concurrency:: run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token) do wyszukiwania pozycji zawierającej daną wartość. Gdy pętla równoległa znajdzie wartość, wywołuje metodę [concurrency:: cancellation_token_source:: Cancel](reference/cancellation-token-source-class.md#cancel) , aby anulować pracę w przyszłości.

[!code-cpp[concrt-parallel-array-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-cancellation-to-break-from-a-parallel-loop_1.cpp)]

Algorytm [concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) działa jednocześnie. W związku z tym nie wykonuje operacji w ustalonej kolejności. Jeśli tablica zawiera wiele wystąpień wartości, wynik może być jednym z jej pozycji.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `parallel-array-search.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

> **CL. exe/EHsc Parallel-Array-Search. cpp**

## <a name="see-also"></a>Zobacz też

[Anulowanie w PPL](cancellation-in-the-ppl.md)<br/>
[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)<br/>
[Funkcja parallel_for](reference/concurrency-namespace-functions.md#parallel_for)<br/>
[cancellation_token_source, klasa](../../parallel/concrt/reference/cancellation-token-source-class.md)
