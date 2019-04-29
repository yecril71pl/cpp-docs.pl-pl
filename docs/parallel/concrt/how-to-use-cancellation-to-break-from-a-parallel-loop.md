---
title: 'Instrukcje: Użyj anulowania aby przerwać pętlę równoległą'
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel search algorithm [Concurrency Runtime]
- parallel search algorithm, writing [Concurrency Runtime]
ms.assetid: 421cd2de-f058-465f-b890-dd8fcc0df273
ms.openlocfilehash: 08f33a75bc5c5391333a2d9368d4ed6563e117c2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346265"
---
# <a name="how-to-use-cancellation-to-break-from-a-parallel-loop"></a>Instrukcje: Użyj anulowania aby przerwać pętlę równoległą

W tym przykładzie pokazano, jak należy używać odwołania do zaimplementowania algorytmu wyszukiwania równoległego podstawowe.

## <a name="example"></a>Przykład

W poniższym przykładzie użyto anulowania, aby wyszukać elementu w tablicy. `parallel_find_any` Używa funkcji [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorytmu i [concurrency::run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token) funkcji wyszukiwania dla pozycji, zawierający danej wartości. Kiedy pętli równoległej znajduje się wartość, wywołuje [concurrency::cancellation_token_source::cancel](reference/cancellation-token-source-class.md#cancel) metodę, aby anulować przyszłych zadań.

[!code-cpp[concrt-parallel-array-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-cancellation-to-break-from-a-parallel-loop_1.cpp)]

[Concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorytm działa jednocześnie. W związku z tym ale nie wykonuje operacje w ustalonej kolejności. Jeśli tablica zawiera wiele wystąpień wartości, wynik może być dowolny z jej położenie.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `parallel-array-search.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**Cl.exe/ehsc równoległych tablicy search.cpp**

## <a name="see-also"></a>Zobacz także

[Anulowanie w PPL](cancellation-in-the-ppl.md)<br/>
[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for Function](reference/concurrency-namespace-functions.md#parallel_for)<br/>
[cancellation_token_source, klasa](../../parallel/concrt/reference/cancellation-token-source-class.md)
