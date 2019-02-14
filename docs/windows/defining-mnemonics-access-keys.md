---
title: Definiowanie wartości i kontrola dostępu
ms.date: 11/04/2016
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
ms.openlocfilehash: 3a885ad57ba05304d51cb45d0b498d81ad37a148
ms.sourcegitcommit: eb2b34a24e6edafb727e87b138499fa8945f981e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2019
ms.locfileid: "56264858"
---
# <a name="defining-control-access-and-values"></a>Definiowanie wartości i kontrola dostępu

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="change-the-tab-order-of-controls"></a>Zmiana kolejności kart kontrolek

Kolejność tabulacji tkwi w kolejności, w którym **kartę** klucz przenosi fokus wprowadzania z jednego formantu do drugiego w oknie dialogowym. Zwykle kolejność tabulacji rozpoczynające się od lewej do prawej i od góry do dołu w oknie dialogowym. Każda kontrolka ma **Tabstop** właściwość, która określa, czy formant uzyskuje fokus wprowadzania.

### <a name="to-set-input-focus-for-a-control"></a>Aby ustawić fokus wprowadzania kontrolki

W [okno właściwości](/visualstudio/ide/reference/properties-window), wybierz opcję **True** lub **False** w **Tabstop** właściwości.

Nawet formantów, które nie mają **Tabstop** właściwością **True** muszą być częścią kolejności tabulacji. Kolejność tabulacji jest ważna, na przykład, gdy użytkownik [Definiowanie kluczy dostępu (Mnemonik)](../windows/defining-mnemonics-access-keys.md) dla formantów, które nie mają podpisy. Statyczny tekst, który zawiera klucz dostępu dla kontrolki powiązane musi bezpośrednio poprzedzać pokrewnej kontrolki w kolejności tabulacji.

> [!NOTE]
> Jeśli Twoje okno dialogowe zawiera nakładające się formanty, zmiana kolejności kart może zmienić sposób wyświetlania kontrolki. Formanty, które później w kolejności tabulacji są zawsze wyświetlane na górze nakładające się formanty, które je poprzedzają w kolejności tabulacji.

### <a name="to-view-the-current-tab-order-for-all-controls-in-a-dialog-box"></a>Aby wyświetlić bieżące kolejność tabulacji dla wszystkich kontrolek w oknie dialogowym

Na **Format** menu, wybierz opcję **kolejność tabulacji**.

\- lub —

- Naciśnij klawisz **Ctrl** + **D**.

### <a name="to-change-the-tab-order-for-all-controls-in-a-dialog-box"></a>Aby zmienić kolejność tabulacji dla wszystkich kontrolek w oknie dialogowym

1. Na **Format** menu, wybierz opcję **kolejność tabulacji**.

   Liczba w lewym górnym rogu każdej kontrolki zawiera jej miejscu w kolejności tabulacji w bieżącym.

1. Ustawianie kolejności tabulacji, klikając pozycję każdej kontrolki w kolejności ma **kartę** klucza do wykonania.

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

2. W [okno właściwości](/visualstudio/ide/reference/properties-window)w **podpis** właściwości, wpisz nową nazwę dla formantu, wpisując handlowe "i" (`&`) przed litery mają jako klucz dostępu dla tej kontrolki. Na przykład `&Radio1`.

3. Naciśnij klawisz **wprowadź**.

   Podkreślenie pojawia się w wyświetlana nazwa, aby wskazać klawisz dostępu, na przykład **R**adio1.

### <a name="to-define-an-access-key-for-a-control-without-a-visible-caption"></a>Aby zdefiniować klawisz dostępu bez podpisu widoczne kontrolki

1. Tworzenie podpisów dla formantu przy użyciu **tekst statyczny** w kontrolce [przybornika](/visualstudio/ide/reference/toolbox).

2. W podpisie tekst statyczny, wpisz znak (`&`) przed litery mają jako klucz dostępu.

3. Upewnij się, że formant statyczny tekst bezpośrednio poprzedza formant, który go etykiety w kolejności tabulacji.

Klucze dostępu w oknie dialogowym powinny być unikatowe.

### <a name="to-check-for-duplicate-access-keys"></a>Aby sprawdzić, czy zduplikowany klucz dostępu

1. Na **Format** menu, kliknij przycisk **Sprawdź mnemonik**.

## <a name="add-values-to-a-combo-box-control"></a>Dodawanie wartości do kontrolki pola kombi

Możesz dodać wartości do kontrolki pola kombi, tak długo, jak masz **okna dialogowego** edytorze.

> [!TIP]
> To dobry pomysł, aby dodać wszystkie wartości do pola kombi *przed* rozmiar, w tym polu **okna dialogowego** edytora lub użytkownik może obciąć tekst, który powinien zostać wyświetlony w kontrolce kombi.

### <a name="to-enter-values-into-a-combo-box-control"></a>Aby wprowadzić wartości do kontrolki pola kombi

1. Zaznacz formant pola kombi, klikając ją.

1. W [okno właściwości](/visualstudio/ide/reference/properties-window), przewiń w dół do **danych** właściwości.

   > [!NOTE]
   > Jeśli wyświetlasz właściwości pogrupowane według typu, **danych** pojawia się w **różne** właściwości.

1. Wybierz obszar wartość dla **danych** właściwości i wpisz wartości danych, oddzielając je średnikami.

   > [!NOTE]
   > Nie umieszczaj spacji między wartościami, ponieważ zakłócać w kolejności alfabetycznej na liście rozwijanej miejsc do magazynowania.

1. Naciśnij klawisz **Enter** po zakończeniu dodawania wartości.

Aby uzyskać informacje na powiększanie część rozwijana pola kombi, zobacz [ustawianie rozmiaru pola kombi i jego listy rozwijanej](setting-the-size-of-the-combo-box-and-its-drop-down-list.md).

> [!NOTE]
> Nie można dodać wartości do projektów Win32 przy użyciu tej procedury ( **danych** właściwość jest wyszarzona dla projektów Win32). Ponieważ projekty Win32 nie ma bibliotek, które dodania tej możliwości, należy dodać wartości do pola kombi w projekcie systemu Win32 programowo.

### <a name="to-test-the-appearance-of-values-in-a-combo-box"></a>Aby przetestować wyświetlania wartości w polu kombi

Po wprowadzeniu wartości w **danych** wybierz **testu** znajdujący się na [paska narzędzi edytora okien dialogowych](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

   Wypróbuj, przewijając w dół listę całej wartości. Wartości wyświetlane dokładnie tak, jak są wpisywane **danych** właściwość **właściwości** okna. Nie ma pisowni lub sprawdzanie wielkość liter.

   Naciśnij klawisz **Esc** aby powrócić do **okno dialogowe** edytora.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)