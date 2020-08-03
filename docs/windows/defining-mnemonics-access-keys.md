---
title: 'Instrukcje: definiowanie dostępu i wartości kontroli (C++)'
ms.date: 02/15/2019
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
ms.openlocfilehash: 91b6365334b977957ff6bd6c25278d4088961a2c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222072"
---
# <a name="how-to-define-control-access-and-values-c"></a>Instrukcje: definiowanie dostępu i wartości kontroli (C++)

## <a name="tab-order"></a>Kolejność tabulacji

Kolejność tabulacji jest kolejnością, w której klawisz **Tab** przenosi fokus wprowadzania z jednej kontrolki do następnego w oknie dialogowym. Zazwyczaj kolejność tabulacji przechodzi od lewej do prawej i od góry do dołu w oknie dialogowym. Każda kontrolka ma właściwość **TabStop** , która określa, czy formant otrzymuje fokus wprowadzania.

- Aby ustawić fokus wprowadzania dla kontrolki, w [oknie właściwości](/visualstudio/ide/reference/properties-window)w właściwości **TabStop** wybierz **wartość PRAWDA** lub **Fałsz** .

Nawet kontrolki, które nie mają właściwości **TabStop** ustawionej na **wartość true** , muszą być częścią kolejności tabulacji, szczególnie w przypadku formantów, które nie mają podpisów. Tekst statyczny, który zawiera klucz dostępu do powiązanej kontrolki, musi bezpośrednio poprzedzać powiązaną kontrolę w kolejności tabulacji.

> [!NOTE]
> Jeśli okno dialogowe zawiera nakładające się kontrolki, zmiana kolejności tabulacji może zmienić sposób wyświetlania kontrolek. Formanty, które są późniejsze w kolejności tabulacji, są zawsze wyświetlane na wszystkich nakładających się kontrolkach, które poprzedzają je w kolejności tabulacji.

- Aby wyświetlić bieżącą kolejność tabulacji dla wszystkich kontrolek, przejdź do menu **Format**  >  **kolejność tabulacji**lub naciśnij klawisz **Ctrl**  +  **D**.

   Liczba w lewym górnym rogu każdej kontrolki pokazuje jej miejsce w bieżącej kolejności tabulacji.

- Aby zmienić kolejność tabulacji dla wszystkich kontrolek, przejdź do menu **Format**  >  **kolejność kart** i ustaw kolejność tabulacji, wybierając poszczególne kontrolki w kolejności, w której ma następować klawisz **Tab** .

- Aby zmienić kolejność tabulacji dla dwóch lub więcej kontrolek, przejdź do menu **Format**  >  **kolejność tabulacji**. Przytrzymaj klawisz **Ctrl** i wybierz kontrolkę, w której rozpocznie się zmiana w kolejności, a następnie zwolnij klawisz **Ctrl** i wybierz kontrolki w kolejności, w której ma następować klawisz **Tab** .

   Na przykład jeśli chcesz zmienić kolejność kontrolek, przytrzymaj wciśnięty `7` klawisz `9` **Ctrl**, a następnie wybierz pozycję Kontrola `6` jako pierwsza.

- Aby ustawić określony formant na numer `1` lub pierwszy w kolejności tabulacji, kliknij dwukrotnie formant.

> [!TIP]
> Po wprowadzeniu trybu **kolejności tabulacji** naciśnij klawisz **ESC** lub **Enter** , aby wyjść z trybu **kolejności kart** i wyłączyć możliwość zmiany kolejności tabulacji.

## <a name="mnemonics-access-keys"></a>Symboli (klawisze dostępu)

Zwykle Użytkownicy klawiatury przesuwają fokus wprowadzania z jednej kontrolki do innej w oknie dialogowym z klawiszami **Tab** i **strzałkami** . Można jednak zdefiniować klucz dostępu (lub łatwą do zapamiętania nazwę), który umożliwia użytkownikom wybranie kontrolki przez naciśnięcie jednego klawisza.

### <a name="to-define-an-access-key-for-a-control-with-a-visible-caption-push-buttons-check-boxes-and-radio-buttons"></a>Aby zdefiniować klucz dostępu dla kontrolki z widocznym podpisem (przyciski push, pola wyboru i przyciski radiowe)

1. Zaznacz kontrolkę w oknie dialogowym.

1. W [oknie właściwości](/visualstudio/ide/reference/properties-window)w właściwości **Caption** wpisz nową nazwę kontrolki, wpisując znak handlowego "i" ( `&` ) przed literą, która ma być kluczem dostępu dla tego formantu. Na przykład `&Radio1`.

1.  Naciśnij klawisz **Enter**.

   W wyświetlonym nagłówku zostanie wyświetlone podkreślenie wskazujące na klucz dostępu, na przykład **R**adio1.

### <a name="to-define-an-access-key-for-a-control-without-a-visible-caption"></a>Aby zdefiniować klucz dostępu dla kontrolki bez widocznego podpisu

1. Utwórz podpis dla kontrolki przy użyciu **statycznej kontrolki tekstowej** w [przyborniku](/visualstudio/ide/reference/toolbox).

1. W podpisie tekst statyczny wpisz znak handlowego "i" ( `&` ) przed literą, która ma być kluczem dostępu.

1. Upewnij się, że formant tekstu statycznego bezpośrednio poprzedza formant, który jest etykietą w kolejności tabulacji.

> [!NOTE]
> Wszystkie klucze dostępu w oknie dialogowym powinny być unikatowe. Aby sprawdzić zduplikowane klucze dostępu, przejdź do pozycji menu **Formatowanie**  >  **Check Mnemonics**.

## <a name="combo-box-values"></a>Wartości pola kombi

Możesz dodać wartości do kontrolki pola kombi, o ile jest otwarty **Edytor okien dialogowych** .

> [!TIP]
> Dobrym pomysłem jest dodanie wszystkich wartości do pola kombi *przed przystąpieniem* do pola w **edytorze okien dialogowych**lub obcinaniem tekstu, który powinien być wyświetlany w kontrolce kombi.

### <a name="to-enter-values-into-a-combo-box-control"></a>Aby wprowadzić wartości do kontrolki pola kombi

1. Wybierz kontrolkę pole kombi, wybierając ją.

1. W [oknie właściwości](/visualstudio/ide/reference/properties-window)przewiń w dół do właściwości **dane** .

   > [!NOTE]
   > Jeśli są wyświetlane właściwości pogrupowane według typu, **dane** są wyświetlane we właściwościach **różne** .

1. Wybierz obszar wartości dla właściwości **dane** i wpisz wartości danych, rozdzielając je średnikami.

   > [!NOTE]
   > Nie należy umieszczać spacji między wartościami, ponieważ spacje zakłócają alphabetizing na liście rozwijanej.

1. Naciśnij klawisz **Enter** po zakończeniu dodawania wartości.

Aby uzyskać informacje na temat powiększania części listy rozwijanej pola kombi, zobacz [Ustawianie rozmiaru pola kombi i jego listy rozwijanej](setting-the-size-of-the-combo-box-and-its-drop-down-list.md).

> [!NOTE]
> Nie można dodawać wartości do projektów Win32 przy użyciu tej procedury (Właściwość **Data** jest wyszarzona dla projektów Win32). Ponieważ projekty Win32 nie mają bibliotek, które dodają tę możliwość, należy programowo dodać wartości do pola kombi z projektem Win32.

### <a name="to-test-the-appearance-of-values-in-a-combo-box"></a>Aby przetestować wygląd wartości w polu kombi

1. Po wprowadzeniu wartości we właściwości **dane** wybierz przycisk **Testuj** na [pasku narzędzi edytora okien dialogowych](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

1. Spróbuj przewinięcie w dół listy całych wartości. Wartości są wyświetlane dokładnie tak, jak zostały wpisane we właściwości **dane** w oknie **Właściwości** . Nie ma sprawdzania pisowni ani wielkich liter.

1. Naciśnij klawisz **ESC** , aby powrócić do edytora **okien dialogowych** .

## <a name="radio-button-values"></a>Wartości przycisków radiowych

Po dodaniu przycisków radiowych do okna dialogowego Traktuj je jako grupę, ustawiając właściwość **grupy** w oknie **Właściwości** dla pierwszego przycisku w grupie. Identyfikator kontrolki dla tego przycisku radiowego pojawia się w [Kreatorze dodawania zmiennej składowej](../ide/add-member-variable-wizard.md), co umożliwia dodanie zmiennej składowej dla grupy przycisków radiowych.

Można mieć więcej niż jedną grupę przycisków radiowych w oknie dialogowym. Dodaj każdą grupę, wykonując poniższą procedurę.

### <a name="to-add-a-group-of-radio-buttons-to-a-dialog-box"></a>Aby dodać grupę przycisków radiowych do okna dialogowego

1. Wybierz kontrolkę przycisk radiowy w [oknie przybornika](/visualstudio/ide/reference/toolbox) i wybierz lokalizację w oknie dialogowym, w której ma zostać umieszczony formant.

1. Powtórz ten krok, aby dodać dowolną liczbę przycisków radiowych. Upewnij się, że przyciski radiowe w grupie są kolejne w kolejności tabulacji.

1. W [oknie właściwości](/visualstudio/ide/reference/properties-window)ustaw właściwość **Grupa** *pierwszego* przycisku radiowego w kolejności tabulacji na **true**.

   Zmiana właściwości **grupy** na **True** powoduje dodanie WS_GROUP stylu do wpisu przycisku w obiekcie okna dialogowego skryptu zasobu i uniemożliwia użytkownikowi wybranie więcej niż jednego przycisku radiowego w danej chwili w grupie przycisków (Jeśli użytkownik wybierze jeden przycisk radiowy, inne w grupie są wyczyszczone).

   > [!NOTE]
   > Tylko pierwszy przycisk radiowy w grupie powinien mieć właściwość **Group** ustawioną na **wartość true**. Jeśli masz dodatkowe kontrolki, które nie są częścią grupy przycisków, ustaw właściwość **grupy** pierwszej kontrolki, *która znajduje się poza grupą* na **wartość true** . Możesz szybko identyfikować pierwszą kontrolkę poza grupą, używając **klawisza Ctrl** + **D** , aby wyświetlić kolejność tabulacji.

### <a name="to-add-a-member-variable-for-the-radio-button-group"></a>Aby dodać zmienną członkowską dla grupy przycisków radiowych

1. Kliknij prawym przyciskiem myszy pierwszą kontrolkę przycisk radiowy w kolejności tabulacji (formant dominujący i jeden z właściwością **grupy** ustawioną na **true**) i wybierz polecenie **Dodaj zmienną**.

1. W [Kreatorze dodawania zmiennej członkowskiej](../ide/add-member-variable-wizard.md)zaznacz pole wyboru **zmienna kontroli** , a następnie wybierz przycisk radiowy **wartość** .

   - W polu **Nazwa zmiennej** wpisz nazwę nowej zmiennej członkowskiej.

   - W polu listy **Typ zmiennej** wybierz **`int`** lub wpisz *int*.

   Teraz można zmodyfikować kod, aby określić, który przycisk radiowy powinien zostać wybrany. Na przykład `m_radioBox1 = 0;` wybiera pierwszy przycisk radiowy w grupie.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Zarządzanie kontrolkami okien dialogowych](controls-in-dialog-boxes.md)<br/>
[Instrukcje: Dodawanie, edytowanie lub usuwanie kontrolek](adding-editing-or-deleting-controls.md)<br/>
[Instrukcje: kontrolki układu](arrangement-of-controls-on-dialog-boxes.md)<br/>
