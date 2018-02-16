---
title: C++ AMP (C++ Accelerated Massive Parallelism) | Dokumentacja firmy Microsoft
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
- C++ AMP (see C++ Accelerated Massive Parallelism)
- C++ Accelerated Massive Parallelism, getting started
ms.assetid: e27824cb-3167-409b-8c3f-a0e476d8f349
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 514c45599bce85bf66bf473ac597dab255888ba8
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="c-amp-c-accelerated-massive-parallelism"></a>C++ AMP (C++ Accelerated Massive Parallelism)
C++ AMP (C++ Accelerated Massive Parallelism) przyspiesza wykonywania kodu C++, wykorzystując sprzętu równoległe danych, która najczęściej występuje jako jednostka przetwarzania graficznych (GPU) na karcie odrębne grafika. Model programowania C++ AMP obsługuje tablice wielowymiarowe indeksowania transfer pamięci i ustawianie widoku kafelków. Obejmuje on też bibliotekę matematyczna funkcji. Można użyć rozszerzenia języka C++ AMP kontrolować sposób przenoszenia danych z Procesora do procesora GPU i wykonać ich kopię.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Przegląd C++ AMP](../../parallel/amp/cpp-amp-overview.md)|W tym artykule opisano najważniejsze funkcje C++ AMP i bibliotekę matematyczna.|  
|[Używanie wyrażeń lambda, obiektów Function i funkcji z ograniczeniami](../../parallel/amp/using-lambdas-function-objects-and-restricted-functions.md)|Informacje dotyczące używania wyrażeń lambda, obiektów function i funkcji z ograniczeniami w wywołaniach [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) metody.|  
|[Użycie fragmentów](../../parallel/amp/using-tiles.md)|Informacje dotyczące używania Kafelki w celu przyspieszenia kodu C++ AMP.|  
|[Używanie akceleratora i obiektów accelerator_view](../../parallel/amp/using-accelerator-and-accelerator-view-objects.md)|Informacje dotyczące używania akceleratorów, aby dostosować wykonywania kodu na procesorze GPU.|  
|[Korzystanie z C++ AMP w aplikacjach platformy uniwersalnej systemu Windows](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)|W tym artykule opisano sposób korzystania z C++ AMP w aplikacjach systemu Windows platformy Uniwersalnej, które używają typów środowiska wykonawczego systemu Windows.|  
|[Grafika (C++ AMP)](../../parallel/amp/graphics-cpp-amp.md)|Opisuje sposób korzystania z C++ AMP grafiki biblioteki.|  
|[Przewodnik: mnożenie macierzy](../../parallel/amp/walkthrough-matrix-multiplication.md)|Pokazuje mnożenie macierzy przy użyciu kodu C++ AMP i ustawianie widoku kafelków.|  
|[Przewodnik: debugowanie aplikacji C++ AMP](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)|Opisano sposób tworzenia i debugowania aplikacji, która używa równoległych redukcji do podsumowania dużą tablicę liczb całkowitych.|  
  
## <a name="reference"></a>Tematy pomocy  
 [Dokumentacja (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)  
  
 [tile_static, słowo kluczowe](../../cpp/tile-static-keyword.md)  
  
 [ograniczenie (C++ AMP)](../../cpp/restrict-cpp-amp.md)  
  
## <a name="other-resources"></a>Inne zasoby  
 [Programowanie równoległe w blogu kodu natywnego](http://go.microsoft.com/fwlink/p/?linkid=238472)  
  
 [C++ AMP przykładowych projektach do pobrania](http://go.microsoft.com/fwlink/p/?linkid=248508)  
  
 [Analizowanie kodu C++ AMP z narzędzia Concurrency Visualizer](http://go.microsoft.com/fwlink/p/?linkid=253987&clcid=0x409)

