---
title: C++ AMP (C++ Accelerated Massive Parallelism) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- C++ AMP (see C++ Accelerated Massive Parallelism)
- C++ Accelerated Massive Parallelism, getting started
ms.assetid: e27824cb-3167-409b-8c3f-a0e476d8f349
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a990acd8f27be476ce35d682a19912dcc85bbeed
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2018
ms.locfileid: "42466130"
---
# <a name="c-amp-c-accelerated-massive-parallelism"></a>C++ AMP (C++ Accelerated Massive Parallelism)
C++ AMP (C++ Accelerated Massive Parallelism) przyspiesza wykonywanie kodu C++ wykorzystując sprzęt danych równoległych powszechnie występujący jako jednostka przetwarzania grafiki (GPU) na dyskretną kartę graficzną. Model programowania C++ AMP obsługuje Wielowymiarowe tablice, indeksowanie, transfer pamięci oraz fragmentację. Zawiera także bibliotekę funkcji matematycznych. Możesz użyć rozszerzeń języka C++ AMP do kontrolowania sposobu przenoszenia danych z procesora CPU do procesora GPU i kopii.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Przegląd C++ AMP](../../parallel/amp/cpp-amp-overview.md)|W tym artykule opisano kluczowe funkcje C++ AMP oraz bibliotekę funkcji matematycznych.|  
|[Używanie wyrażeń lambda, obiektów Function i funkcji z ograniczeniami](../../parallel/amp/using-lambdas-function-objects-and-restricted-functions.md)|Opisuje sposób używania wyrażeń lambda, obiektów funkcyjnych i funkcji z ograniczeniami w wywołaniach [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) metody.|  
|[Użycie fragmentów](../../parallel/amp/using-tiles.md)|W tym artykule opisano sposób używania fragmentacji w celu przyspieszenia kodu C++ AMP.|  
|[Używanie akceleratora i obiektów accelerator_view](../../parallel/amp/using-accelerator-and-accelerator-view-objects.md)|Opisuje sposób używania akceleratorów, aby dostosować wykonanie kodu na procesorze GPU.|  
|[Korzystanie z C++ AMP w aplikacjach platformy uniwersalnej systemu Windows](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)|W tym artykule opisano, jak używać biblioteki C++ AMP w aplikacjach platformy uniwersalnej Windows (UWP), które używają typów środowiska wykonawczego Windows.|  
|[Grafika (C++ AMP)](../../parallel/amp/graphics-cpp-amp.md)|Opisuje sposób używania biblioteki funkcji graficznych C++ AMP.|  
|[Przewodnik: mnożenie macierzy](../../parallel/amp/walkthrough-matrix-multiplication.md)|Pokazuje mnożenie macierzy za pomocą kodu C++ AMP i fragmentacji.|  
|[Przewodnik: debugowanie aplikacji C++ AMP](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)|Opis sposobu tworzenia i debugowania aplikacji korzystającej z równoległych redukcji do zsumowania dużą tablicę liczb całkowitych.|  
  
## <a name="reference"></a>Tematy pomocy  

[Odwołanie (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)    
[tile_static — słowo kluczowe](../../cpp/tile-static-keyword.md)    
[ograniczenie (C++ AMP)](../../cpp/restrict-cpp-amp.md)  
  
## <a name="other-resources"></a>Inne zasoby  
 
[Programowanie równoległe w kodzie macierzystym bloga](http://go.microsoft.com/fwlink/p/?linkid=238472)  
[C++ AMP przykładowe projekty do pobrania](http://go.microsoft.com/fwlink/p/?linkid=248508)  
[Analizowanie kodu C++ AMP w narzędziu Concurrency Visualizer](http://go.microsoft.com/fwlink/p/?linkid=253987&clcid=0x409)