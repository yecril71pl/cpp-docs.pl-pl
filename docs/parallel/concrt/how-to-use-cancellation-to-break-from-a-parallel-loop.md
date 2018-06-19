---
title: 'Porady: Użyj anulowania, aby przerwać pętlę równoległą | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- writing a parallel search algorithm [Concurrency Runtime]
- parallel search algorithm, writing [Concurrency Runtime]
ms.assetid: 421cd2de-f058-465f-b890-dd8fcc0df273
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b1b5153c225c3bb3a67be4265cf8303da2121c2b
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33696295"
---
# <a name="how-to-use-cancellation-to-break-from-a-parallel-loop"></a>Porady: użyj anulowania, aby przerwać pętlę równoległą
Ten przykład przedstawia sposób użycia anulowania do zaimplementowania algorytmu wyszukiwania równoległego podstawowe.  
  
## <a name="example"></a>Przykład  

 W poniższym przykładzie użyto anulowania, aby wyszukać element w tablicy. `parallel_find_any` Używa [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorytmu i [concurrency::run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token) funkcja wyszukiwania pozycji, która zawiera podanej wartości. Kiedy równoległej pętli znajduje się wartość, wywołuje [concurrency::cancellation_token_source::cancel](reference/cancellation-token-source-class.md#cancel) metodę, aby anulować pracy w przyszłości.  


  
 [!code-cpp[concrt-parallel-array-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-cancellation-to-break-from-a-parallel-loop_1.cpp)]  
  

 [Concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorytm działa jednocześnie. W związku z tym nie są wykonywane operacje w ustalonej kolejności. Jeśli tablica zawiera wiele wystąpień wartości, wynik może być jeden z jego położenia.  

  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `parallel-array-search.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **Cl.exe/ehsc równoległe tablicy search.cpp**  
  
## <a name="see-also"></a>Zobacz też  
 [Anulowanie w PPL](cancellation-in-the-ppl.md)   
 [Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)   
 [parallel_for — funkcja](reference/concurrency-namespace-functions.md#parallel_for)   
 [cancellation_token_source, klasa](../../parallel/concrt/reference/cancellation-token-source-class.md)
