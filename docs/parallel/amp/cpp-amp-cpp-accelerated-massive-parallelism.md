---
title: C++ AMP (C++ Accelerated Massive Parallelism)
ms.date: 11/04/2016
helpviewer_keywords:
- C++ AMP (see C++ Accelerated Massive Parallelism)
- C++ Accelerated Massive Parallelism, getting started
ms.assetid: e27824cb-3167-409b-8c3f-a0e476d8f349
ms.openlocfilehash: 243c476b6536278eb09b26b24becb65276d6e48a
ms.sourcegitcommit: 093f49b8b69daf86661adc125b1d2d7b1f0e0650
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2020
ms.locfileid: "89427637"
---
# <a name="c-amp-c-accelerated-massive-parallelism"></a>C++ AMP (C++ Accelerated Massive Parallelism)

C++ AMP (C++ Accelerated Massive Parallelism) przyspiesza wykonywanie kodu C++ dzięki wykorzystaniu sprzętu równoległego danych, który jest powszechnie obecny jako procesor graficzny (GPU) na dyskretnej karcie graficznej. Model programowania C++ AMP obejmuje obsługę tablic wielowymiarowych, indeksowania, transferu pamięci i dzielenia. Zawiera również bibliotekę funkcji matematycznych. Za pomocą rozszerzeń języka C++ AMP można kontrolować sposób przenoszenia danych z procesora CPU do procesora GPU i z powrotem.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Przegląd C++ AMP](../../parallel/amp/cpp-amp-overview.md)|Opisuje najważniejsze funkcje C++ AMP i biblioteki matematycznej.|
|[Używanie wyrażeń lambda, obiektów funkcyjnych i funkcji z ograniczeniami](../../parallel/amp/using-lambdas-function-objects-and-restricted-functions.md)|Opisuje, jak używać wyrażeń lambda, obiektów funkcyjnych i funkcji ograniczonych w wywołaniach metody [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) .|
|[Używanie kafelków](../../parallel/amp/using-tiles.md)|Opisuje sposób używania kafelków w celu przyspieszenia kodu C++ AMP.|
|[Korzystanie z akceleratorów i accelerator_view obiektów](../../parallel/amp/using-accelerator-and-accelerator-view-objects.md)|Opisuje sposób użycia akceleratorów w celu dostosowania wykonywania kodu na procesorze GPU.|
|[Używanie C++ AMP w aplikacjach platformy UWP](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)|Opisuje sposób używania C++ AMP w aplikacjach platforma uniwersalna systemu Windows (platformy UWP), które używają typów środowisko wykonawcze systemu Windows.|
|[Grafika (C++ AMP)](../../parallel/amp/graphics-cpp-amp.md)|Opisuje sposób używania biblioteki grafiki C++ AMP.|
|[Przewodnik: mnożenie macierzy](../../parallel/amp/walkthrough-matrix-multiplication.md)|Ilustruje mnożenie macierzy przy użyciu kodu C++ AMP i dzielenia.|
|[Przewodnik: debugowanie aplikacji C++ AMP](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)|Wyjaśnia, jak utworzyć i debugować aplikację, która korzysta z obniżenia równoległego do sumowania dużych tablic liczb całkowitych.|

## <a name="reference"></a>Dokumentacja

[Odwołanie (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)<br/>
[tile_static — słowo kluczowe](../../cpp/tile-static-keyword.md)<br/>
[ograniczenie (C++ AMP)](../../cpp/restrict-cpp-amp.md)

## <a name="other-resources"></a>Inne zasoby

[Programowanie równoległe w kodzie natywnym blogu](/archive/blogs/nativeconcurrency/)<br/>
[C++ AMP przykładowe projekty do pobrania](/archive/blogs/nativeconcurrency/c-amp-sample-projects-for-download)<br/>
[Analizowanie kodu C++ AMP za pomocą wizualizatora współbieżności](/archive/blogs/nativeconcurrency/analyzing-c-amp-code-with-the-concurrency-visualizer)
