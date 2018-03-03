---
title: "Porady: pisanie pętli parallel_for | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- writing a parallel_for loop [Concurrency Runtime]
- parallel_for function, example
ms.assetid: adb4d64e-5514-4b70-8dcb-b9210e6b5a1c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 60ae6b7f496f86bde91801e486315587fb693436
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-write-a-parallelfor-loop"></a>Porady: pisanie pętli parallel_for
W tym przykładzie przedstawiono sposób użycia [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) do obliczenia produktu macierzy dwa.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono `matrix_multiply` funkcji, która oblicza iloczyn dwóch macierzy kwadratowych.  
  
 [!code-cpp[concrt-parallel-matrix-multiply#1](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_1.cpp)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono `parallel_matrix_multiply` funkcji, która używa `parallel_for` algorytm zewnętrzne pętli równolegle.  
  
 [!code-cpp[concrt-parallel-matrix-multiply#2](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_2.cpp)]  
  
 W tym przykładzie parallelizes zewnętrzne pętli, tylko ponieważ wykonuje wystarczająco dużo pracy do korzystania z obciążenie przetwarzania równoległego. Jeśli parallelize wewnętrzny pętli, nie otrzymasz przyrost wydajności ponieważ mała ilość pracy, który wykonuje pętli wewnętrznej nie rozwiązać obciążenie przetwarzania równoległego. W związku z tym parallelizing zewnętrzne pętli jest tylko najlepszy sposób, aby zmaksymalizować korzyści współbieżności na większości systemów.  
  
## <a name="example"></a>Przykład  
 Następujące bardziej szczegółowy przykład porównuje wydajność `matrix_multiply` funkcji w porównaniu z `parallel_matrix_multiply` funkcji.  
  
 [!code-cpp[concrt-parallel-matrix-multiply#3](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_3.cpp)]  
  
 Następujące przykładowe dane wyjściowe jest dla komputera, który ma cztery procesory.  
  
```Output  
serial: 3853  
parallel: 1311  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby skompilować kod, skopiuj go i następnie wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `parallel-matrix-multiply.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **Cl.exe/ehsc równoległe macierzy multiply.cpp**  
  
## <a name="see-also"></a>Zobacz też  
 [Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)   
 [parallel_for — funkcja](reference/concurrency-namespace-functions.md#parallel_for)


