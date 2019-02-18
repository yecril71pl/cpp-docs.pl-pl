---
title: Definiowanie wartości i kontrola dostępu
ms.date: 02/15/2019
f1_keywords:
- vc.editors.dialog.combo
helpviewer_keywords:
- access keys [C++], adding
- keyboard shortcuts [C++], controls
- dialog box controls [C++], mnemonics
- access keys [C++], checking
- mnemonics [C++], checking for duplicate
- mnemonics
- mnemonics [C++], dialog box controls
- keyboard shortcuts [C++], uniqueness checking
- Check Mnemonics command
- controls [C++], access keys
- access keys [C++]
- combo boxes [C++], Data property
- controls [C++], testing values in combo boxes
- combo boxes [C++], adding values
- combo boxes [C++], previewing values
- Data property
- combo boxes [C++], testing values
ms.assetid: 60a85435-aa30-4c5c-98b6-42fb045b9eb2
ms.openlocfilehash: 20319cd08d6d1e77faef1275e63bf3ffd354356b
ms.sourcegitcommit: 24592ba0a38c7c996ffd3d55fe1024231a59ccc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2019
ms.locfileid: "56336491"
---
# <a name="defining-control-access-and-values"></a>Definiowanie wartości i kontrola dostępu

## <a name="change-the-tab-order-of-controls"></a>Zmiana kolejności kart kontrolek

Kolejność tabulacji tkwi w kolejności, w którym **kartę** klucz przenosi fokus wprowadzania z jednego formantu do drugiego w oknie dialogowym. Zwykle kolejność tabulacji rozpoczynające się od lewej do prawej i od góry do dołu w oknie dialogowym. Każda kontrolka ma **Tabstop** właściwość, która określa, czy formant uzyskuje fokus wprowadzania.

### <a name="to-set-input-focus-for-a-control"></a>Aby ustawić fokus wprowadzania kontrolki

W [okno właściwości](/visualstudio/ide/reference/properties-window), wybierz opcję **True** lub **False** w **Tabstop** właściwości.

Nawet formantów, które nie mają **Tabstop** właściwością **True** muszą być częścią kolejności tabulacji. Kolejność tabulacji jest ważna, na przykład, gdy użytkownik [Definiowanie kluczy dostępu (Mnemonik)](../windows/defining-mnemonics-access-keys.md) dla formantów, które nie mają podpisy. Statyczny tekst, który zawiera klucz dostępu dla kontrolki powiązane musi bezpośrednio poprzedzać pokrewnej kontrolki w kolejności tabulacji.

> [!NOTE]
> Jeśli Twoje okno dialogowe zawiera nakładające się formanty, zmiana kolejności kart może zmienić sposób wyświetlania kontrolki. Formanty, które później w kolejności tabulacji są zawsze wyświetlane na górze nakładające się formanty, które je poprzedzają w kolejności tabulacji.

### <a name="to-view-the-current-tab-order-for-all-controls-in-a-dialog-box"></a>Aby wyświetlić bieżące kolejność tabulacji dla wszystkich kontrolek w oknie dialogowym

Przejdź do **Format** menu, a następnie wybierz **kolejność tabulacji**, lub naciśnij **Ctrl** + **D**.

### <a name="to-change-the-tab-order-for-all-controls-in-a-dialog-box"></a>Aby zmienić kolejność tabulacji dla wszystkich kontrolek w oknie dialogowym

1. Na **Format** menu, wybierz opcję **kolejność tabulacji**.

   Liczba w lewym górnym rogu każdej kontrolki zawiera jej miejscu w kolejności tabulacji w bieżącym.

1. Ustaw kolejność tabulacji, wybierając każdy formant w kolejności, mają **kartę** klucza do wykonania.

1. Naciśnij klawisz **Enter** aby zakończyć działanie **kolejność tabulacji** trybu.

   > [!TIP]
   > Po wprowadzeniu **kolejność tabulacji** tryb, możesz nacisnąć przycisk **Esc** lub **Enter** wyłączyć możliwość zmiany kolejności tabulacji.

### <a name="to-change-the-tab-order-for-two-or-more-controls"></a>Aby zmienić kolejność tabulacji dla co najmniej dwóch formantów

1. Z **Format** menu, wybierz **kolejność tabulacji**.

1. Określ, gdzie rozpoczyna się zmiany w kolejności. Najpierw naciśnij i przytrzymaj **Ctrl** klucza i wybierz kontrolkę, a następnie wybierz subskrypcję, w którym zmiany kolejności do rozpoczęcia.

   Na przykład, jeśli chcesz zmienić kolejność formantów `7` za pośrednictwem `9`, naciśnij i przytrzymaj **Ctrl**, następnie wybierz kontrolkę `6` pierwszy.

   > [!NOTE]
   > Aby ustawić numer określonej kontrolki `1` (pierwszy w kolejności tabulacji), kliknij dwukrotnie formant.

1. Wersja **Ctrl** klucza, a następnie wybierz kontrolki, w kolejności, ma **kartę** klawisz, aby wykonać kroki od tego momentu.

1. Naciśnij klawisz **Enter** aby zakończyć działanie **kolejność tabulacji** trybu.

## <a name="define-mnemonics-access-keys"></a>Definiowanie mnemonik (klucze dostępu)

Zazwyczaj użytkownicy klawiatury przeniesienie fokusu wprowadzania z jednego formantu do drugiego w oknie dialogowym z **kartę** i **strzałkę** kluczy. Jednak można zdefiniować klawisz dostępu (nazwa mnemoników lub łatwa do zapamiętania) umożliwiający użytkownikom na wybór formantu przez naciśnięcie klawisza pojedynczego.

### <a name="to-define-an-access-key-for-a-control-with-a-visible-caption-push-buttons-check-boxes-and-radio-buttons"></a>Aby zdefiniować klucza dostępu dla formantu za pomocą widoczne podpis (przyciski, pola wyboru i przyciski radiowe)

1. Wybierz kontrolkę w oknie dialogowym.

1. W [okno właściwości](/visualstudio/ide/reference/properties-window)w **podpis** właściwości, wpisz nową nazwę dla formantu, wpisując handlowe "i" (`&`) przed litery mają jako klucz dostępu dla tej kontrolki. Na przykład `&Radio1`.

1. Naciśnij klawisz **wprowadź**.

   Podkreślenie pojawia się w wyświetlana nazwa, aby wskazać klawisz dostępu, na przykład **R**adio1.

### <a name="to-define-an-access-key-for-a-control-without-a-visible-caption"></a>Aby zdefiniować klawisz dostępu bez podpisu widoczne kontrolki

1. Tworzenie podpisów dla formantu przy użyciu **tekst statyczny** w kontrolce [przybornika](/visualstudio/ide/reference/toolbox).

1. W podpisie tekst statyczny, wpisz znak (`&`) przed litery mają jako klucz dostępu.

1. Upewnij się, że formant statyczny tekst bezpośrednio poprzedza formant, który go etykiety w kolejności tabulacji.

> [!NOTE]
> Klucze dostępu w oknie dialogowym powinny być unikatowe. Aby sprawdzić, czy zduplikowany klucz dostępu, przejdź do **Format** menu, a następnie wybierz **Sprawdź mnemonik**.

## <a name="combo-box-values"></a>Wartości pola kombi

Możesz dodać wartości do kontrolki pola kombi, tak długo, jak masz **okna dialogowego** edytorze.

> [!TIP]
> To dobry pomysł, aby dodać wszystkie wartości do pola kombi *przed* rozmiar, w tym polu **okna dialogowego** edytora lub użytkownik może obciąć tekst, który powinien zostać wyświetlony w kontrolce kombi.

### <a name="to-enter-values-into-a-combo-box-control"></a>Aby wprowadzić wartości do kontrolki pola kombi

1. Wybierz formant pola kombi, wybierając ją.

1. W [okno właściwości](/visualstudio/ide/reference/properties-window), przewiń w dół do **danych** właściwości.

   > [!NOTE]
   > Jeśli wyświetlasz właściwości pogrupowane według typu, **danych** pojawia się w **różne** właściwości.

1. Wybierz obszar wartość dla **danych** właściwości i wpisz wartości danych, oddzielając je średnikami.

   > [!NOTE]
   > Nie należy umieszczać spacji między wartościami, ponieważ zakłócać w kolejności alfabetycznej na liście rozwijanej miejsc do magazynowania.

1. Naciśnij klawisz **Enter** po zakończeniu dodawania wartości.

Aby uzyskać informacje na powiększanie część rozwijana pola kombi, zobacz [ustawianie rozmiaru pola kombi i jego listy rozwijanej](setting-the-size-of-the-combo-box-and-its-drop-down-list.md).

> [!NOTE]
> Nie można dodać wartości do projektów Win32 przy użyciu tej procedury ( **danych** właściwość jest wyszarzona dla projektów Win32). Ponieważ projekty Win32 nie ma bibliotek, które dodania tej możliwości, należy dodać wartości do pola kombi w projekcie systemu Win32 programowo.

### <a name="to-test-the-appearance-of-values-in-a-combo-box"></a>Aby przetestować wyświetlania wartości w polu kombi

Po wprowadzeniu wartości w **danych** wybierz **testu** znajdujący się na [paska narzędzi edytora okien dialogowych](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

   Wypróbuj, przewijając w dół listę całej wartości. Wartości wyświetlane dokładnie tak, jak są wpisywane **danych** właściwość **właściwości** okna. Nie ma pisowni lub sprawdzanie wielkość liter.

   Naciśnij klawisz **Esc** aby powrócić do **okno dialogowe** edytora.

   Teraz można edytować swój kod, aby określić, który przycisk radiowy powinien zostaną wyświetlone jako zaznaczone. Na przykład `m_radioBox1 = 0;` wybiera pierwszy przycisk radiowy w grupie.
Teraz można edytować swój kod, aby określić, który przycisk radiowy powinien zostaną wyświetlone jako zaznaczone. Na przykład `m_radioBox1 = 0;` wybiera pierwszy przycisk radiowy w grupie.

## <a name="radio-button-values"></a>Przycisk radiowy wartości

Po dodaniu przycisków radiowych w oknie dialogowym je traktować jako grupa, ustawiając **grupy** właściwość **właściwości** okna dla pierwszego przycisku w grupie. Pojawi się w polu Identyfikator kontrolki, dla tego przycisku radiowego [Kreator dodawania zmiennej składowej](../ide/add-member-variable-wizard.md), co pozwala dodać zmienną członkowską, grupy przycisków radiowych.

Może mieć więcej niż jedna grupa przycisków radiowych w oknie dialogowym. Dodaj każdej grupy, korzystając z następującej procedury.

### <a name="to-add-a-group-of-radio-buttons-to-a-dialog-box"></a>Aby dodać grupę przycisków radiowych w oknie dialogowym

1. Zaznacz formant przycisku radiowego w [okno przybornika](/visualstudio/ide/reference/toolbox) i wybierz lokalizację znajdującą się w oknie dialogowym, gdzie umieścić formant.

1. Powtórz powyższy krok, aby dodać dowolną liczbę przyciski radiowe, ile potrzebujesz. Upewnij się, że przyciski radiowe w grupie są następujące po sobie w kolejności tabulacji.

1. W [okno właściwości](/visualstudio/ide/reference/properties-window)ustaw **grupy** właściwość *pierwszy* przycisku radiowego w kolejności tabulacji na **True**.

   Zmiana **grupy** właściwości **True** dodaje WS_GROUP styl do przycisku wpis obiektu okna dialogowego skryptu zasobu i uniemożliwia wybranie więcej niż jednego przycisku radiowego w danym momencie przez użytkownika mogą Grupa przycisków (Jeśli użytkownik wybiera jeden przycisk radiowy, inne osoby w grupie zostaną wyczyszczone).

   > [!NOTE]
   > Tylko pierwszy przycisk radiowy w grupie powinny mieć **grupy** właściwością **True**. Jeśli masz dodatkowe formanty, które nie są częścią grupy przycisk, ustaw **grupy** właściwość pierwszy formant *jest spoza grupy* do **True** także. Można szybko określić pierwszą kontrolkę spoza grupy za pomocą **Ctrl**+**D** Aby wyświetlić kolejność tabulacji.

### <a name="to-add-a-member-variable-for-the-radio-button-group"></a>Aby dodać zmiennej składowej w grupie przycisków radiowych

1. Kliknij prawym przyciskiem myszy pierwszą kontrolkę przycisku radiowego w kolejności tabulacji (formant dominujący i z **grupy** właściwością **True**) i wybierz polecenie **Dodaj zmienną** z menu skrótów.

1. W [Kreator dodawania zmiennej składowej](../ide/add-member-variable-wizard.md), wybierz opcję **zmienna sterująca** pole wyboru, a następnie wybierz **wartość** przycisku radiowego.

1. W **nazwa zmiennej** wpisz nazwę dla nowej zmiennej elementu członkowskiego.

1. W **typ zmiennej** pola listy, wybierz opcję **int** lub typ *int*.

   Teraz można edytować swój kod, aby określić, który przycisk radiowy powinien zostaną wyświetlone jako zaznaczone. Na przykład `m_radioBox1 = 0;` wybiera pierwszy przycisk radiowy w grupie.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)