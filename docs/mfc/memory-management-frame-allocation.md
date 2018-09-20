---
title: 'Zarządzanie pamięcią: Klatki, Alokacja | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- memory leaks [MFC], frame allocation
- memory [MFC], detecting leaks
- memory [MFC], reclaiming
- memory allocation [MFC], frames
- frame variables [MFC], automatic deletion of
- scope [MFC], frame variables
- heap allocation [MFC], vs. frame allocation
- variables [MFC], frame variables
- memory leaks [MFC], detecting
- memory, releasing [MFC]
- stack frames [MFC]
- memory leaks [MFC], allocating objects on the frame
- detecting memory leaks [MFC]
- frame allocation [MFC]
- frame variables [MFC]
ms.assetid: 945a211a-6f4f-4679-bb6a-b0f2a0d4a6c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ca2d98898c232cdb65d3ac5d1288b06aca403772
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398121"
---
# <a name="memory-management-frame-allocation"></a>Zarządzanie pamięcią: alokacja ramek

Alokacji na ramce przyjmuje jego nazwę z "ramki stosu", o które ustawiono zawsze, gdy funkcja jest wywoływana. Ramka stosu jest to obszar pamięci, który tymczasowo przechowuje argumenty do funkcji, jak również wszelkie zmienne, które są zdefiniowane lokalne do funkcji. Zmienne ramek są często nazywane zmiennymi "Automatyczny", ponieważ kompilator automatycznie przydziela miejsce dla nich.

Istnieją dwa główne cechy ramkę alokacji. Najpierw podczas definiowania zmiennej lokalnej, wystarczająca ilość miejsca jest przydzielany na ramce stosu, aby pomieścić całą zmiennej, nawet jeśli jest on dużą tablicę lub struktury danych. Po drugie zmienne ramek są automatycznie usuwane po przejściu poza zakresem:

[!code-cpp[NVC_MFC_Utilities#10](../mfc/codesnippet/cpp/memory-management-frame-allocation_1.cpp)]

Dla zmiennych lokalnych funkcji to przejście zakresu występuje, gdy wyjścia funkcji, ale zakres zmiennej ramki może być mniejszy niż funkcja, jeśli używane są zagnieżdżonych nawiasów klamrowych. Bardzo ważne jest to automatyczne wykrywanie zmienne ramek. W przypadku prostych typów pierwotnych (takie jak **int** lub **bajtów**), tablic lub struktur danych, automatyczne wykrywanie po prostu odzyskuje pamięć używaną przez zmienną. Ponieważ zmienna stała się poza zakresem, nie są dostępne w mimo to. W przypadku obiektów języka C++ jednak proces automatycznego usuwania jest nieco bardziej skomplikowane.

Gdy obiekt jest zdefiniowany jako zmienna ramki, jego konstruktor jest wywoływana automatycznie w momencie, w którym występuje definicja. Gdy obiekt wykracza poza zakres, jego destruktor jest wywoływana automatycznie, zanim pamięci dla obiektu są odzyskiwane. To automatyczne konstrukcje i zniszczenie ruchu może być bardzo przydatne, ale należy pamiętać, automatyczne wywołań, szczególnie w celu destruktor.

Zaletą alokowania obiektów w ramce jest, że są automatycznie usuwane. Podczas alokowania obiektów na ramce, nie trzeba martwić się o obiektach zapomniane, powodując przecieków pamięci. (Aby uzyskać szczegółowe informacje dotyczące przecieki pamięci, zobacz artykuł [wykrywania przecieków pamięci w MFC](/previous-versions/visualstudio/visual-studio-2010/c99kz476\(v=vs.100\)).) Alokacja ramek niedogodność polega na tym, że zmienne ramek nie można używać poza ich zakresem. Innym czynnikiem w wyborze ramkę alokacji i Alokacja sterty dla dużych struktur i obiektów, jest często lepiej używać sterty zamiast stosu magazynu, ponieważ obszar stosu często jest ograniczona.

## <a name="see-also"></a>Zobacz też

[Zarządzanie pamięcią](../mfc/memory-management.md)

