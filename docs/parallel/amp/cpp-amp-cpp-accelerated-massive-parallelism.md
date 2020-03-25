---
title: C++ AMP (C++ Accelerated Massive Parallelism)
ms.date: 11/04/2016
helpviewer_keywords:
- C++ AMP (see C++ Accelerated Massive Parallelism)
- C++ Accelerated Massive Parallelism, getting started
ms.assetid: e27824cb-3167-409b-8c3f-a0e476d8f349
ms.openlocfilehash: c9ef7ab816ec0d17b9dc0b569a6f3a43af83cc68
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167696"
---
# <a name="c-amp-c-accelerated-massive-parallelism"></a>C++ AMP (C++ Accelerated Massive Parallelism)

C++AMP (C++ przyspieszanie ogromnej współbieżności) przyspiesza wykonywanie C++ kodu przez skorzystanie z zalet sprzętu równoległego danych, który jest powszechnie obecny jako procesor graficzny (GPU) na dyskretnej karcie graficznej. Model C++ programowania amp obejmuje obsługę tablic wielowymiarowych, indeksowania, transferu pamięci i dzielenia. Zawiera również bibliotekę funkcji matematycznych. Za pomocą C++ rozszerzeń języka amp można kontrolować sposób przenoszenia danych z procesora CPU do procesora GPU i z powrotem.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Przegląd C++ AMP](../../parallel/amp/cpp-amp-overview.md)|Opisuje najważniejsze funkcje C++ amp i biblioteki matematycznej.|
|[Używanie wyrażeń lambda, obiektów Function i funkcji z ograniczeniami](../../parallel/amp/using-lambdas-function-objects-and-restricted-functions.md)|Opisuje, jak używać wyrażeń lambda, obiektów funkcyjnych i funkcji ograniczonych w wywołaniach metody [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) .|
|[Użycie fragmentów](../../parallel/amp/using-tiles.md)|Opisuje sposób używania kafelków w celu przyspieszenia C++ kodu amp.|
|[Używanie akceleratora i obiektów accelerator_view](../../parallel/amp/using-accelerator-and-accelerator-view-objects.md)|Opisuje sposób użycia akceleratorów w celu dostosowania wykonywania kodu na procesorze GPU.|
|[Korzystanie z C++ AMP w aplikacjach platformy uniwersalnej systemu Windows](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)|Opisuje sposób używania C++ AMP w platforma uniwersalna systemu Windows aplikacji (platformy UWP), które używają typów środowisko wykonawcze systemu Windows.|
|[Grafika (C++ AMP)](../../parallel/amp/graphics-cpp-amp.md)|Opisuje sposób korzystania z C++ biblioteki graficznej amp.|
|[Przewodnik: mnożenie macierzy](../../parallel/amp/walkthrough-matrix-multiplication.md)|Pokazuje mnożenie macierzy przy użyciu C++ kodu amp i rozmieszczanie.|
|[Przewodnik: debugowanie aplikacji C++ AMP](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)|Wyjaśnia, jak utworzyć i debugować aplikację, która korzysta z obniżenia równoległego do sumowania dużych tablic liczb całkowitych.|

## <a name="reference"></a>Dokumentacja

[Dokumentacja (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)<br/>
[tile_static, słowo kluczowe](../../cpp/tile-static-keyword.md)<br/>
[ograniczenie (C++ AMP)](../../cpp/restrict-cpp-amp.md)

## <a name="other-resources"></a>Inne zasoby

[Programowanie równoległe w kodzie natywnym blogu](https://go.microsoft.com/fwlink/p/?linkid=238472)<br/>
[C++Przykładowe projekty AMP do pobrania](https://go.microsoft.com/fwlink/p/?linkid=248508)<br/>
[Analizowanie C++ kodu amp przy użyciu wizualizatora współbieżności](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/03/09/analyzing-c-amp-code-with-the-concurrency-visualizer/)
