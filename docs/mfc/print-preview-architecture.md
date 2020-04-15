---
title: Architektura podglądu wydruku
ms.date: 11/04/2016
helpviewer_keywords:
- print preview [MFC], process
- previewing printing
- print preview [MFC], architecture
- printing [MFC], print preview
- print preview [MFC], modifications to MFC
ms.assetid: 0efc87e6-ff8d-43c5-9d72-9b729a169115
ms.openlocfilehash: 5943edc22cd48ed10d152f72624467ff87104b96
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375944"
---
# <a name="print-preview-architecture"></a>Architektura podglądu wydruku

W tym artykule wyjaśniono, jak struktura MFC implementuje funkcje podglądu wydruku. Omawiane tematy to m.in.:

- [Proces podglądu wydruku](#_core_the_print_preview_process)

- [Modyfikowanie podglądu wydruku](#_core_modifying_print_preview)

Podgląd wydruku różni się nieco od wyświetlania ekranu i drukowania, ponieważ zamiast bezpośrednio rysować obraz na urządzeniu, aplikacja musi symulować drukarkę za pomocą ekranu. Aby to uwzględnić, biblioteka klas Programu Microsoft Foundation definiuje specjalną (nieudokumentowaną) klasę pochodzącą z [klasy CDC](../mfc/reference/cdc-class.md), o nazwie `CPreviewDC`. Wszystkie `CDC` obiekty zawierają dwa konteksty urządzenia, ale zazwyczaj są identyczne. W `CPreviewDC` obiekcie są one różne: pierwszy reprezentuje symulowaną drukarkę, a drugi reprezentuje ekran, na którym faktycznie jest wyświetlany wynik.

## <a name="the-print-preview-process"></a><a name="_core_the_print_preview_process"></a>Proces podglądu wydruku

Gdy użytkownik wybierze polecenie Podgląd wydruku z menu `CPreviewDC` **Plik,** struktura tworzy obiekt. Za każdym razem, gdy aplikacja wykonuje operację, która ustawia charakterystykę kontekstu urządzenia drukarki, struktura wykonuje również podobną operację w kontekście urządzenia ekranu. Jeśli na przykład aplikacja wybierze czcionkę do drukowania, w ramach zostanie wybrana czcionka do wyświetlania na ekranie, która symuluje czcionkę drukarki. Za każdym razem, gdy aplikacja będzie wysyłać dane wyjściowe do drukarki, struktura zamiast wysyła dane wyjściowe na ekranie.

Podgląd wydruku różni się również od drukowania w kolejności, w. Podczas drukowania struktura kontynuuje pętlę drukowania, dopóki nie zostanie renderowany określony zakres stron. Podczas podglądu wydruku jedna lub dwie strony są wyświetlane w dowolnym momencie, a następnie aplikacja czeka; nie są wyświetlane żadne dalsze strony, dopóki użytkownik nie odpowie. Podczas podglądu wydruku aplikacja musi również odpowiadać na WM_PAINT wiadomości, tak jak podczas zwykłego wyświetlania ekranu.

[Funkcja CView::OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) jest wywoływana podczas wywoływania trybu podglądu, tak jak na początku zadania drukowania. [Struktura CPrintInfo](../mfc/reference/cprintinfo-structure.md) przeniesiona do funkcji zawiera kilka elementów członkowskich, których wartości można ustawić, aby dostosować niektóre cechy operacji podglądu wydruku. Na przykład można ustawić *m_nNumPreviewPages* element członkowski, aby określić, czy chcesz wyświetlić podgląd dokumentu w trybie jednostronicowym czy dwustronicowym.

## <a name="modifying-print-preview"></a><a name="_core_modifying_print_preview"></a>Modyfikowanie podglądu wydruku

Zachowanie i wygląd podglądu wydruku można dość łatwo zmodyfikować na wiele sposobów. Na przykład, można, między innymi:

- W oknie podglądu wydruku pojawi się pasek przewijania, który ułatwia dostęp do dowolnej strony dokumentu.

- Przyczyna podglądu wydruku, aby utrzymać pozycję użytkownika w dokumencie, rozpoczynając jego wyświetlanie na bieżącej stronie.

- W celu podglądu i drukowania należy wykonać inną inicjalizację.

- Spowoduje to, że podgląd wydruku będzie wyświetlał numery stron we własnych formatach.

Jeśli wiesz, jak długo jest `SetMaxPage` dokument i wywołać z odpowiednią wartością, ramach można użyć tych informacji w trybie podglądu, jak również podczas drukowania. Gdy struktura zna długość dokumentu, może zapewnić okno podglądu z paskiem przewijania, dzięki czemu użytkownik może przeglądać dokument w trybie podglądu. Jeśli nie ustawiono długości dokumentu, struktura nie może umieścić pole przewijania, aby wskazać bieżącą pozycję, więc struktura nie dodaje paska przewijania. W takim przypadku użytkownik musi użyć przycisków Następna strona i Poprzednia strona na pasku sterowania okna podglądu, aby przeglądać dokument.

W przypadku podglądu wydruku przydatne może okazać *m_nCurPage* się przypisanie `CPrintInfo`wartości do m_nCurPage elementu członkowskiego , nawet jeśli nigdy nie zrobisz tego w przypadku zwykłego drukowania. Podczas zwykłego drukowania ten element członkowski przenosi informacje z struktury do klasy widoku. W ten sposób struktura informuje widok, która strona powinna być drukowana.

Natomiast po uruchomieniu trybu podglądu wydruku *m_nCurPage* element członkowski przenosi informacje w przeciwnym kierunku: z widoku do struktury. Struktura używa wartości tego elementu członkowskiego, aby określić, która strona powinna być najpierw wyświetlona w podglądzie. Domyślną wartością tego elementu członkowskiego jest 1, więc pierwsza strona dokumentu jest wyświetlana początkowo. Można zastąpić, `OnPreparePrinting` aby ustawić ten element członkowski na numer strony wyświetlanej w momencie wywoływania polecenia Podgląd wydruku. W ten sposób aplikacja zachowuje bieżącą pozycję użytkownika podczas przechodzenia z normalnego trybu wyświetlania do trybu podglądu wydruku.

Czasami można `OnPreparePrinting` wykonać różne inicjowanie w zależności od tego, czy jest to wywoływane dla zadania drukowania lub podglądu wydruku. Można to określić, badając *zmienną m_bPreview* elementu `CPrintInfo` członkowskiego w strukturze. Ten element członkowski jest ustawiony na **WARTOŚĆ PRAWDA** podczas wywoływania podglądu wydruku.

Struktura `CPrintInfo` zawiera również element członkowski o nazwie *m_strPageDesc*, który służy do formatowania ciągów wyświetlanych u dołu ekranu w trybie jednostronicowym i wielostronicowym. Domyślnie te ciągi są w formie "Page *n"* i "Pages *n* - *m*", ale można zmodyfikować *m_strPageDesc* od wewnątrz `OnPreparePrinting` i ustawić ciągi na coś bardziej skomplikowane. Zobacz [CPrintInfo struktury](../mfc/reference/cprintinfo-structure.md) w *odwołaniu MFC, aby* uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz też

[Drukowanie i podgląd wydruku](../mfc/printing-and-print-preview.md)<br/>
[Drukowanie](../mfc/printing.md)<br/>
[Klasa CView](../mfc/reference/cview-class.md)<br/>
[Klasa CDC](../mfc/reference/cdc-class.md)
