---
title: Funkcje członkowskie formantu suwaka
ms.date: 11/04/2016
helpviewer_keywords:
- CSliderCtrl class [MFC], methods
- slider controls [MFC], member functions
ms.assetid: dbde49ee-7306-4d14-a6ce-d09aa198178f
ms.openlocfilehash: 25414b1d98c87c67c1dc8e13bb44bdc25869db94
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472651"
---
# <a name="slider-control-member-functions"></a>Funkcje członkowskie formantu suwaka

Aplikacja może wywołać suwaka, funkcje składowe kontrolki, aby pobrać informacje o kontrolce suwaka ([z CSliderCtrl](../mfc/reference/csliderctrl-class.md)) i zmienić jego właściwości.

Aby pobrać położenie suwaka (czyli wartość użytkownik wybierze), użyj [GetPos](../mfc/reference/csliderctrl-class.md#getpos) funkcja elementu członkowskiego. Aby ustawić położenie suwaka, użyj [SetPos](../mfc/reference/csliderctrl-class.md#setpos) funkcja elementu członkowskiego. W dowolnym momencie można użyć `VerifyPos` funkcja elementu członkowskiego, aby upewnić się, że suwak jest między minimalne i maksymalne wartości.

Zakres kontrolki suwaka ustawiono ciągłe wartości, które mogą reprezentować kontrolki suwaka. Większość aplikacji używa [SetRange](../mfc/reference/csliderctrl-class.md#setrange) funkcję elementu członkowskiego, aby ustawić zakres kontrolki suwaka, podczas jej pierwszego tworzenia. Aplikacje można dynamicznie zmieniać zakresu, po utworzeniu kontrolki suwaka, za pomocą [SetRangeMax](../mfc/reference/csliderctrl-class.md#setrangemax) i [SetRangeMin](../mfc/reference/csliderctrl-class.md#setrangemin) funkcji elementów członkowskich. Aplikacja, która umożliwia zakresu, które mają być zmienione dynamicznie zazwyczaj pobiera ustawienia końcowej zakresu po użytkownik zakończył pracę z kontrolką suwaka. Aby pobrać te ustawienia, należy użyć [getrange —](../mfc/reference/csliderctrl-class.md#getrange), [GetRangeMax](../mfc/reference/csliderctrl-class.md#getrangemax), i [GetRangeMin](../mfc/reference/csliderctrl-class.md#getrangemin) funkcji elementów członkowskich.

Aplikacja może użyć stylu TBS_AUTOTICKS mieć znaczniki kontrolki suwaka wyświetlane automatycznie. Jeśli aplikacja musi kontrolować położenia lub częstotliwość znaczników, jednak wiele elementów członkowskich może służyć.

Aby ustawić położenie znaczników głównyc, aplikacja może użyć [SetTic](../mfc/reference/csliderctrl-class.md#settic) funkcja elementu członkowskiego. [SetTicFreq](../mfc/reference/csliderctrl-class.md#setticfreq) funkcja elementu członkowskiego umożliwia aplikacji ustaw znaczników znaków, które pojawiają się w regularnych odstępach czasu w zakresie formant suwaka. Na przykład aplikacja można używać tej funkcji elementu członkowskiego do wyświetlenia tylko 10 znaczniki w zakresie od 1 do 100.

Aby uzyskać indeks zakresu odpowiadający znacznika, należy użyć [GetTic](../mfc/reference/csliderctrl-class.md#gettic) funkcja elementu członkowskiego. [GetTicArray](../mfc/reference/csliderctrl-class.md#getticarray) funkcja elementu członkowskiego pobiera tablicę tych indeksów. Aby pobrać położenie znaczników głównyc w współrzędne klienta użyj [GetTicPos](../mfc/reference/csliderctrl-class.md#getticpos) funkcja elementu członkowskiego. Aplikacja może pobrać liczbę znaczników przy użyciu [GetNumTics](../mfc/reference/csliderctrl-class.md#getnumtics) funkcja elementu członkowskiego.

[ClearTics](../mfc/reference/csliderctrl-class.md#cleartics) funkcja członkowska usuwa wszystkie znaczniki kontrolki suwaka.

Rozmiar wiersza w kontrolce suwaka Określa, jak daleko przenosi suwaka, gdy aplikacja otrzymuje komunikat z powiadomieniem TB_LINEDOWN lub TB_LINEUP. Podobnie rozmiar strony określa odpowiedzi na komunikaty powiadomień TB_PAGEDOWN i TB_PAGEUP. Aplikacje można pobierać i ustawiać wartości rozmiaru wiersza i strony za pomocą [GetLineSize](../mfc/reference/csliderctrl-class.md#getlinesize), [SetLineSize](../mfc/reference/csliderctrl-class.md#setlinesize), [GetPageSize](../mfc/reference/csliderctrl-class.md#getpagesize), i [SetPageSize](../mfc/reference/csliderctrl-class.md#setpagesize) funkcji elementów członkowskich.

Aplikacja może użyć funkcji elementów członkowskich do pobrania wymiarów kontrolki suwaka. [GetThumbRect](../mfc/reference/csliderctrl-class.md#getthumbrect) funkcja elementu członkowskiego pobiera prostokąt otaczający potrzeby suwaka. [GetChannelRect](../mfc/reference/csliderctrl-class.md#getchannelrect) funkcja elementu członkowskiego pobiera prostokąt otaczający dla kanału kontroli suwaka. (Kanał jest obszar przenosi suwaka i zawierającą podświetlenie po wybraniu zakresu).

Jeśli formant suwaka ma styl TBS_ENABLESELRANGE, użytkownik może wybrać zakres sąsiadujących wartości z niego. Liczba elementów członkowskich umożliwiają wybranego zakresu dynamicznego dostosowania. [SetSelection](../mfc/reference/csliderctrl-class.md#setselection) funkcja elementu członkowskiego ustawia początkową i końcową pozycję zaznaczenia. Gdy użytkownik zakończy, ustawienie zaznaczony zakres, aplikacja może pobrać ustawienia za pomocą [GetSelection](../mfc/reference/csliderctrl-class.md#getselection) funkcja elementu członkowskiego. Aby wyczyścić wybranych przez użytkownika, należy użyć [ClearSel](../mfc/reference/csliderctrl-class.md#clearsel) funkcja elementu członkowskiego.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CSliderCtrl](../mfc/using-csliderctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

