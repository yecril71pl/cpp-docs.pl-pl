---
title: 'Zarządzanie pamięcią: alokacja ramek'
ms.date: 11/04/2016
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
ms.openlocfilehash: 1ecf1c08164d1a760fce62457a6019e767ed2605
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626300"
---
# <a name="memory-management-frame-allocation"></a>Zarządzanie pamięcią: alokacja ramek

Alokacja w ramce przyjmuje swoją nazwę z "ramki stosu", która jest ustawiana za każdym razem, gdy wywoływana jest funkcja. Ramka stosu jest obszarem pamięci, który tymczasowo przechowuje argumenty do funkcji, a także wszelkie zmienne, które są zdefiniowane lokalnie dla funkcji. Zmienne ramek są często nazywane zmiennymi "automatycznymi", ponieważ kompilator automatycznie przydziela miejsce dla nich.

Istnieją dwie kluczowe cechy alokacji ramek. Najpierw podczas definiowania zmiennej lokalnej w ramce stosu jest przypisywany wystarczająco dużo miejsca, aby pomieścić całą zmienną, nawet jeśli jest to duża tablica lub struktura danych. Po drugie, zmienne ramki są automatycznie usuwane, gdy wykraczają poza zakres:

[!code-cpp[NVC_MFC_Utilities#10](codesnippet/cpp/memory-management-frame-allocation_1.cpp)]

W przypadku zmiennych funkcji lokalnych to przejście zakresu odbywa się po zakończeniu funkcji, ale zakres zmiennej ramki może być mniejszy niż funkcja, jeśli są używane zagnieżdżone nawiasy klamrowe. To automatyczne usuwanie zmiennych ramek jest bardzo ważne. W przypadku prostych typów pierwotnych (takich jak **int** lub **Byte**), tablic lub struktur danych automatyczne usuwanie po prostu ponownie przejmuje pamięć używaną przez zmienną. Ponieważ zmienna została wypada poza zakresem, nie można do niej uzyskać dostępu. Jednak w przypadku obiektów C++ proces automatycznego usuwania jest nieco bardziej skomplikowany.

Gdy obiekt jest zdefiniowany jako zmienna ramki, jego Konstruktor jest automatycznie wywoływany w punkcie, w którym znajduje się definicja. Gdy obiekt wykracza poza zakres, jego destruktor jest automatycznie wywoływany przed odzyskiwaniem pamięci dla obiektu. Ta automatyczna konstrukcja i niszczenie może być bardzo przydatne, ale należy pamiętać o automatycznym wykorzystaniu, szczególnie dla destruktora.

Główną zaletą alokowania obiektów w ramce jest to, że są one automatycznie usuwane. Po przydzieleniu obiektów do ramki nie trzeba martwić się o zapomniane obiekty powodujące przecieki pamięci. (Szczegółowe informacje o przeciekach pamięci znajdują się [w artykule Wykrywanie przecieków pamięci w MFC](/previous-versions/visualstudio/visual-studio-2010/c99kz476(v=vs.100))). Wadą alokacji ramki jest to, że zmienne ramek nie mogą być używane poza ich zakresem. Innym czynnikiem podczas wybierania alokacji ramek i alokacji sterty jest to, że w przypadku dużych struktur i obiektów często lepiej jest używać sterty zamiast stosu dla magazynu, ponieważ przestrzeń stosu jest często ograniczona.

## <a name="see-also"></a>Zobacz też

[Zarządzanie pamięcią](memory-management.md)
