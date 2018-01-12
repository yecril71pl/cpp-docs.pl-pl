---
title: "Porady: Użyj anulowania, aby przerwać pętlę równoległą | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- writing a parallel search algorithm [Concurrency Runtime]
- parallel search algorithm, writing [Concurrency Runtime]
ms.assetid: 421cd2de-f058-465f-b890-dd8fcc0df273
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 27c6b4a216609c788978e4b857b5996587f899f2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
