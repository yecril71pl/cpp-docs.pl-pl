---
title: Dodawanie, edytowanie lub usuwanie kontrolek
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog.dialog
- vc.controls.activex
- vc.editors.dialog.insertActiveXControls
helpviewer_keywords:
- Dialog Editor [C++], creating controls
- dialog boxes [C++], adding controls to
- Toolbox [C++], Dialog Editor tab
- controls [C++], types
- syslink controls in dialog boxes
- custom controls [C++], dialog boxes
- controls [C++], standard
- Dialog Editor [C++], creating controls
- controls [C++], adding to dialog boxes
- controls [C++], adding multiple
- dialog box controls [C++], size
- controls [C++], sizing
- dialog boxes [C++], adding ActiveX controls
- ActiveX controls [C++], adding to dialog boxes
- Insert ActiveX Control dialog box [C++]
- controls [C++], editing properties
- ActiveX controls [C++], properties
- controls [C++], undoing changes
- controls [C++], editing properties
- dialog box controls [C++], editing properties
- dialog box controls [C++], deleting
- controls [C++], deleting
- Dialog Editor [C++], default control events
- controls [C++], default control events
- events [C++], controls
- dialog box controls [C++], events
- member variables, defining for controls
- variables, dialog box control member variables
- controls [C++], member variables
- Dialog Editor [C++], defining member variables for controls
ms.assetid: 73cef03f-5c8c-456a-87d1-1458dff185cf
ms.openlocfilehash: b4edb5b7a51e4f6d368759ebc2e05a1cc585f19a
ms.sourcegitcommit: 52c05e10b503e834c443ef11e7ca1987e332f876
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742755"
---
# <a name="adding-editing-or-deleting-controls"></a>Dodawanie, edytowanie lub usuwanie kontrolek

Za pomocą **okna dialogowego** edytora, możesz dodać, zmienić rozmiar, edytowanie i usuwanie kontrolki w oknach dialogowych. Można również edytować właściwości kontrolki, takie jak jego identyfikator lub czy jest początkowo widoczne w czasie wykonywania.

**Edytor okien dialogowych** karta jest wyświetlana w [okno przybornika](/visualstudio/ide/reference/toolbox) podczas pracy **okna dialogowego** edytora. Można również dostosować **przybornika** okna do użytku łatwiejsze. Aby uzyskać więcej informacji, zobacz [korzystanie z przybornika](/visualstudio/ide/using-the-toolbox) i [Pokaż lub Ukryj okno przybornika](showing-or-hiding-the-dialog-editor-toolbar.md).

Możesz użyć menu skrótów w **okna dialogowego** edytora, aby szybko dodać zarejestrowany kontrolek ActiveX do okna dialogowego i można dodać formanty ActiveX do **przybornika** Aby uzyskać szybki dostęp.

Formanty standardowe dostępne w **przybornika** z domyślną zdarzenia są:

|Nazwa kontrolki|Domyślne zdarzenia|
|---|---|
|[Kontrolka przycisku](../mfc/reference/cbutton-class.md)|BN_CLICKED|
|[Kontrolka pola wyboru](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[Kontrolka pola kombi](../mfc/reference/ccombobox-class.md)|CBN_SELCHANGE|
|[Edytuj kontrolkę](../mfc/reference/cedit-class.md)|EN_CHANGE|
|Pole grupy|(Nie dotyczy)|
|[Kontrolka pola listy](../mfc/reference/clistbox-class.md)|LBN_SELCHANGE|
|[Kontrolka przycisku radiowego](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[Kontrolka tekstu statycznego](../mfc/reference/cstatic-class.md)|(Nie dotyczy)|
|[Formant obrazu](../mfc/reference/cpictureholder-class.md)|(Nie dotyczy)|
|[Kontrolka 2.0 edycji wzbogaconej](../mfc/using-cricheditctrl.md)|EN_CHANGE|
|[Pasek przewijania](../mfc/reference/cscrollbar-class.md)|NM_THEMECHANGED|

Aby uzyskać więcej informacji na temat korzystania z **RichEdit 1.0** kontrolką MFC, zobacz [używanie formantu RichEdit 1.0 z MFC](../windows/using-the-richedit-1-0-control-with-mfc.md) i [przykłady formantów edycji wzbogaconej](../mfc/rich-edit-control-examples.md).

[Wspólnych formantów Windows](../mfc/controls-mfc.md) dostępne w **przybornika** zapewniają większą funkcjonalność w aplikacji. Obejmują one:

|Nazwa kontrolki|Domyślne zdarzenia|
|---|---|
|[Kontrolka suwaka](../mfc/slider-control-styles.md)|NM_CUSTOMDRAW|
|[Kontrolki pokrętła](../mfc/using-cspinbuttonctrl.md)|UDN_DELTAPOS|
|[Kontrolki postępu](../mfc/styles-for-the-progress-control.md)|NM_CUSTOMDRAW|
|[Formantu klawisza dostępu](../mfc/using-a-hot-key-control.md)|NM_OUTOFMEMORY —|
|[Kontrolka listy](../mfc/list-control-and-list-view.md)|LVN_ITEMCHANGE|
|[Kontrolka drzewa](../mfc/tree-control-styles.md)|TVN_SELCHANGE|
|[Kontrolki karty](../mfc/tab-controls-and-property-sheets.md)|TCN_SELCHANGE|
|[Kontrolki animacji](../mfc/using-an-animation-control.md)|ACN_START|
|[Kontrolka czasu selektora daty](../mfc/creating-the-date-and-time-picker-control.md)|DTN_DATETIMECHANGE|
|[Kontrolowanie kalendarza miesięcznego](../mfc/month-calendar-control-examples.md)|MCN_SELCHANGE|
|[Formant adresu IP](../mfc/reference/cipaddressctrl-class.md)|IPN_FIELDCHANGED|
|[Rozszerzone formant pola kombi](../mfc/creating-an-extended-combo-box-control.md)||
|[Kontrolka niestandardowa](custom-controls-in-the-dialog-editor.md)|TTN_GETDISPINFO|

Aby uzyskać więcej informacji, zobacz [klasy kontrolek](../mfc/control-classes.md), [klasy okien dialogowych](../mfc/dialog-box-classes.md), i [Style paska przewijania](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles).

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-add-a-control"></a>Aby dodać kontrolkę

Aby dodać formanty do Twojego nowego okna dialogowego, przeciągnij formanty z **przybornika** do okna dialogowego, który tworzysz. Możesz przenosić kontrolki lub zmieniać ich rozmiar i kształt.

Można dodać niestandardowe formanty do okna dialogowego wybierając **kontrolki niestandardowej** ikonę **przybornika** i przeciągając je do swojej okna dialogowego. Aby dodać **Syslink** , Dodaj formant niestandardowy, a następnie zmienić formant **klasy** właściwości **Syslink**. Ta akcja spowoduje, że właściwości, aby odświeżyć i Pokaż **Syslink** właściwości formantu. Aby uzyskać informacji na temat klasy otoki MFC, zobacz [CLinkCtrl](../mfc/reference/clinkctrl-class.md).

### <a name="to-add-a-control-to-a-dialog-box"></a>Aby dodać formant do okna dialogowego

1. Upewnij się, że z kartami okno dialogowe bieżącego dokumentu w ramce edytora. Jeśli okno dialogowe nie jest bieżącym dokumencie, nie będziesz widzieć **Karta Edytor okien dialogowych** w **przybornika**.

1. Na **Edytor okien dialogowych** karcie **przybornika** okna, wybierz kontrolkę, należy następnie:

   Wybierz okno dialogowe, w lokalizacji, w którym chcesz umieścić formant. Ten formant jest widoczny, gdy wybrano.

   \- lub —

   Przeciąganie i upuszczanie formantu z **przybornika** okna do lokalizacji na Twoje okno dialogowe.

   \- lub —

   Kliknij dwukrotnie formant w **przybornika** okna (jest wyświetlana na dialogowym), a następnie zmiana położenia kontrolki do lokalizacji, użytkownik sobie tego życzy.

### <a name="to-add-multiple-controls"></a>Aby dodać wiele kontrolek

1. Przytrzymując naciśnięty **Ctrl** klucza, wybierz kontrolkę w **przybornika** okna.

1. Wersja **Ctrl** klucza, a następnie wybierz okno dialogowe dowolną liczbę razy dodać określonego formantu.

1. Naciśnij klawisz **Esc** przestanie umieszczenie kontrolki.

### <a name="to-size-a-control-while-you-add-it"></a>Rozmiar kontrolki podczas dodawania go

1. Wybierz kontrolkę w **przybornika** okna.

1. Umieść kursor w miejscu (która jest wyświetlana jako krzyżowe na ekranie), w której chcesz lewego górnego rogu nowej kontrolki na Twoje okno dialogowe.

1. Wybierz i przytrzymaj naciśnięty przycisk myszy, aby móc zakotwiczyć w lewym górnym rogu formantu w oknie dialogowym, a następnie przeciągnij kursor w prawo i w dół, aż do uzyskania odpowiedni rozmiar kontrolki.

   > [!NOTE]
   > Faktycznie można zakotwiczyć dowolne dowiedzą o formant, który rysowania. Jako przykład tej procedurze użyto lewego górnego rogu.

1. Zwolnij przycisk myszy. Kontrolka jest gotowy do okna dialogowego w podany rozmiar.

   > [!TIP]
   > Można zmienić rozmiar formantu po upuszczenie na okno dialogowe, przenosząc uchwytów zmiany rozmiaru w obramowania formantu. Aby uzyskać więcej informacji, zobacz [ustalanie rozmiaru pojedynczych formantów](../windows/sizing-individual-controls.md).

### <a name="to-add-an-activex-control"></a>Aby dodać formant ActiveX

Program Visual Studio umożliwia wstawianie kontrolki ActiveX z okna dialogowego. Aby uzyskać więcej informacji, zobacz [kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md) i [kontenery kontrolek ActiveX](../mfc/activex-control-containers.md).

**Wstawianie formantu ActiveX** okno dialogowe umożliwia wstawianie kontrolki ActiveX dialogowym podczas korzystania z [Edytor okien dialogowych](../windows/dialog-editor.md). To okno dialogowe zawiera następujące właściwości:

|Właściwość|Opis|
|---|---|
|**ActiveX Control**|Wyświetla listę formantów ActiveX. Wstawianie kontrolki z tego okna dialogowego nie generuje klasę otoki. Klasa otoki, należy użyć [Widok klas](/visualstudio/ide/viewing-the-structure-of-code) ją utworzyć (Aby uzyskać więcej informacji, zobacz [Dodawanie klasy](../ide/adding-a-class-visual-cpp.md)). Jeśli formant ActiveX nie pojawia się w tym oknie dialogowym, spróbuj zainstalować kontroli zgodnie z instrukcjami dostawcy.|
|**Path**|Wyświetla plik, w którym znajduje się Kontrolka ActiveX.|

#### <a name="to-see-the-activex-controls-available"></a>Aby wyświetlić dostępne kontrolki ActiveX

1. Otwórz okno dialogowe, w edytorze okien dialogowych.

1. Kliknij prawym przyciskiem myszy w dowolnym miejscu w treści okno dialogowe.

1. W menu skrótów wybierz **Wstawianie formantu ActiveX**.

   **Wstawianie formantu ActiveX** pojawi się okno dialogowe, przedstawiający wszystkie formanty ActiveX w Twoim systemie. W dolnej części okna dialogowego jest wyświetlana ścieżka do pliku formantu ActiveX.

#### <a name="to-add-an-activex-control-to-a-dialog-box"></a>Aby dodać formant ActiveX do okna dialogowego

1. W **Wstawianie formantu ActiveX** okna dialogowego wybierz kontrolkę, o których chcesz dodać do swojej okno dialogowe, a następnie wybierz pozycję **OK**.

   Formant ma być wyświetlany w oknie dialogowym, w którym można go edytować lub tworzyć programy obsługi dla niego tak samo, jak dowolną inną kontrolką.

   > [!NOTE]
   > Można dodać formanty ActiveX do **przybornika** okna, aby mieć łatwy dostęp.

   > [!CAUTION]
   > Może nie być prawne rozpowszechnianie wszystkich kontrolek ActiveX w Twoim systemie. Zapoznaj się z umową licencyjną dotyczącą oprogramowania, zainstalowanego kontrolki lub skontaktuj się z firmą oprogramowania.

## <a name="to-edit-a-control"></a>Aby edytować kontrolkę

### <a name="to-edit-the-properties-of-a-control-or-controls"></a>Edytowanie właściwości kontrolki lub kontrolki

1. W oknie dialogowym Wybierz formant, który chcesz zmodyfikować.

   > [!NOTE]
   > Jeśli wybierzesz wielu formantów, można edytować tylko właściwości wspólne dla wybranych kontrolek.

1. W [okno właściwości](/visualstudio/ide/reference/properties-window), zmień właściwości formantu.

   > [!NOTE]
   > Po ustawieniu **mapy bitowej** właściwości dla przycisku, przycisk radiowy lub kontrolka pola wyboru równa **True**, styl BS_BITMAP został zaimplementowany dla formantu. Aby uzyskać więcej informacji, zobacz [style przycisku](../mfc/reference/styles-used-by-mfc.md#button-styles). Na przykład kojarzenia mapę bitową z kontrolką zobacz [CButton::SetBitmap](../mfc/reference/cbutton-class.md#setbitmap). Mapy bitowe nie będą wyświetlane na kontrolki, gdy jesteś w **okna dialogowego** Edytor zasobów.

### <a name="to-undo-changes-to-the-properties-of-a-control"></a>Aby cofnąć zmiany do właściwości kontrolki

1. Upewnij się, że kontrolka ma fokus w **okna dialogowego** edytora.

1. Wybierz **Cofnij** z **Edytuj** menu (Jeśli fokus jest na kontrolki, **Cofnij** polecenie jest niedostępne).

### <a name="to-edit-properties-for-an-activex-control"></a>Aby edytować właściwości kontrolki ActiveX

Kontrolki ActiveX, dostarczone przez niezależnych dostawców może są wyposażone w ich własnych właściwości i właściwości. Właściwości formantów ActiveX są wyświetlane w **właściwości** okna. Ponadto żadnych stron właściwości utworzone przez autorów formantu ActiveX są wyświetlane w **strony właściwości** okno dialogowe (Aby wyświetlić **strona właściwości** określonej kontrolki ActiveX, kliknij przycisk **Strona właściwości** znajdujący się w [okno właściwości](/visualstudio/ide/reference/properties-window)).

Na stronie właściwości dla formantu ActiveX, w zależności od arkuszy właściwości, które pochodzą z formantu ActiveX w ramach będą wyświetlane różne karty.

> [!NOTE]
> Poniższa procedura ma zastosowanie przy użyciu strony właściwości, aby edytować kontrolki ActiveX. Możesz również przeglądać i edytować właściwości formantu ActiveX w nowym **właściwości** okna.

1. Wybierz **ActiveX** kontroli.

1. Na **widoku** menu, wybierz opcję **strona właściwości** i Wyświetl właściwości.

1. W razie potrzeby na stronie właściwości, należy wprowadzić zmiany.

### <a name="to-define-a-member-variable-for-a-non-button-dialog-box-control"></a>Aby zdefiniować zmienną składową formantu pola okna dialogowego (inne niż przycisk)

Aby zdefiniować zmienną składową dla dowolnego formantu pola okna dialogowego z wyjątkiem przyciski, można użyć następującej metody.

> [!NOTE]
> Ten proces dotyczy tylko kontrolki okna dialogowego, w ramach projektu MFC. Należy używać w projektach ATL **nowych komunikatów Windows do programów obsługi zdarzeń** okno dialogowe. Aby uzyskać więcej informacji, zobacz [komunikat typy związane z obiektami interfejsu użytkownika](../mfc/reference/message-types-associated-with-user-interface-objects.md), [Edytowanie programu obsługi komunikatów](../mfc/reference/editing-a-message-handler.md), i [Definiowanie obsługi komunikatów dla komunikatów odzwierciedlone](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md).

1. W [Edytor okien dialogowych](../windows/dialog-editor.md), wybierz formant.

1. Podczas naciśnięcie **Ctrl** klucza, kliknij dwukrotnie kontrolka okna dialogowego.

   [Kreator dodawania zmiennej składowej](../ide/add-member-variable-wizard.md) pojawia się.

1. Wpisz odpowiednie informacje w **Dodaj zmienną elementu członkowskiego** kreatora. Aby uzyskać więcej informacji, zobacz [wymiana danych okna dialogowego](../mfc/dialog-data-exchange.md).

1. Wybierz **OK** aby powrócić do **okna dialogowego** edytora.

   > [!TIP]
   > Aby przejść z dowolnego formantu pola okna dialogowego do jego istniejącej procedury obsługi, kliknij dwukrotnie formant.

Można również użyć **zmienne Członkowskie** karcie [Kreator klas MFC](../mfc/reference/mfc-class-wizard.md) do dodawania nowych zmiennych Członkowskich dla określonej klasy i wyświetlanie zmiennych składowych, które zostały już zdefiniowane.

## <a name="to-delete-a-control"></a>Aby usunąć formant

W oknie dialogowym Wybierz formant, a następnie naciśnij klawisz **Usuń** klucza.

   \- lub —

Na **Edytuj** menu, wybierz opcję **Usuń**.

   > [!TIP]
   > Podczas korzystania z **okna dialogowego** edytora w wielu przypadkach, kliknięcie prawym przyciskiem myszy wyświetli menu skrótów z najczęściej używanymi poleceniami.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Kontrolki w oknach dialogowych](controls-in-dialog-boxes.md)<br/>
[Kontrolki okna dialogowego i typy zmiennych](../ide/dialog-box-controls-and-variable-types.md)<br/>
[Pliki zasobów](../windows/resource-files-visual-studio.md)<br/>

<!-- excluded links
[Mapping Messages to Functions](../mfc/reference/mapping-messages-to-functions.md)<br/>
[Adding Functionality with Code Wizards](../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Adding a Class](../ide/adding-a-class-visual-cpp.md)<br/>
[Adding a Member Function](../ide/adding-a-member-function-visual-cpp.md)<br/>
[Adding a Member Variable](../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Overriding a Virtual Function](../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC Message Handler](../mfc/reference/adding-an-mfc-message-handler.md)
[Declaring a Variable Based on Your New Control Class](../mfc/reference/declaring-a-variable-based-on-your-new-control-class.md)<br/>
-->
