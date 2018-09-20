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
ms.openlocfilehash: 0aeaf79ba847474c1a474d53b7d1281421fa23a9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381663"
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

[Dokumentacja (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)<br/>
[tile_static, słowo kluczowe](../../cpp/tile-static-keyword.md)<br/>
[ograniczenie (C++ AMP)](../../cpp/restrict-cpp-amp.md)

## <a name="other-resources"></a>Inne zasoby

[Programowanie równoległe w kodzie macierzystym bloga](http://go.microsoft.com/fwlink/p/?linkid=238472)<br/>
[C++ AMP przykładowe projekty do pobrania](http://go.microsoft.com/fwlink/p/?linkid=248508)<br/>
[Analizowanie kodu C++ AMP w narzędziu Concurrency Visualizer](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/03/09/analyzing-c-amp-code-with-the-concurrency-visualizer/)