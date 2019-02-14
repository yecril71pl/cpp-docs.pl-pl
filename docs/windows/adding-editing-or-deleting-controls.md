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
- controls [C++], troubleshooting
- Dialog Editor [C++], troubleshooting
- dialog boxes [C++], troubleshooting
- InitCommonControls
- RichEdit 1.0 control
- rich edit controls [C++], RichEdit 1.0
ms.assetid: 73cef03f-5c8c-456a-87d1-1458dff185cf
ms.openlocfilehash: 648ac3329409ba221881f75eaa51e1779091b0f0
ms.sourcegitcommit: eb2b34a24e6edafb727e87b138499fa8945f981e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2019
ms.locfileid: "56264871"
---
# <a name="adding-editing-or-deleting-controls"></a>Dodawanie, edytowanie lub usuwanie kontrolek

Za pomocą **okna dialogowego** edytora, możesz dodać, zmienić rozmiar, edytowanie i usuwanie kontrolki w oknach dialogowych. Można również edytować właściwości kontrolki, takie jak jego identyfikator lub czy jest początkowo widoczne w czasie wykonywania.

**Edytor okien dialogowych** karta jest wyświetlana w [okno przybornika](/visualstudio/ide/reference/toolbox) podczas pracy **okna dialogowego** edytora. Można również dostosować **przybornika** okna do użytku łatwiejsze. Aby uzyskać więcej informacji, zobacz [korzystanie z przybornika](/visualstudio/ide/using-the-toolbox) i [Pokaż lub Ukryj okno przybornika](showing-or-hiding-the-dialog-editor-toolbar.md).

Możesz użyć menu skrótów w **okna dialogowego** edytora, aby szybko dodać zarejestrowany kontrolek ActiveX do okna dialogowego i można dodać formanty ActiveX do **przybornika** Aby uzyskać szybki dostęp.

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

## <a name="known-issue"></a>Znany problem

Po dodaniu wspólne kontrolki lub kontrolki edycji wzbogaconej w oknie dialogowym, nie będzie on widoczny podczas testowania okna dialogowego lub nie będzie wyświetlane okno dialogowe, sam.

Aby zobaczyć przykład problemu:

1. Utwórz projekt systemu Win32, modyfikując ustawienia aplikacji, dzięki czemu można utworzyć aplikację Windows (nie Aplikacja konsoli).

1. W [widok zasobów](../windows/resource-view-window.md), kliknij dwukrotnie plik .rc.

1. W obszarze opcji okno dialogowe, kliknij dwukrotnie **o** pole.

1. Dodaj **formant adresu IP** do okna dialogowego.

1. Zapisz i **ponowna kompilacja**.

1. Wykonywanie programu.

1. W oknie dialogowym **pomocy** menu, kliknij przycisk **o** polecenia; nie okno dialogowe zostanie wyświetlone okno.

Obecnie **okna dialogowego** edytora nie dodaje automatycznie kodu do projektu podczas przeciągania i upuszczania następujące formanty standardowe lub formanty edycji wzbogaconej na okno dialogowe. Ani Visual Studio zapewnia błąd lub ostrzeżenie w przypadku wystąpienia tego problemu. Aby rozwiązać problem, należy ręcznie dodać kodu dla formantu.

||||
|-|-|-|
|Kontrolka suwaka|Kontrolka drzewa|Wybór daty i godziny|
|Kontrolki pokrętła|Kontrolki karty|Kalendarza miesięcznego|
|Kontrolki postępu|Kontrolki animacji|Formant adresu IP|
|Klawisz skrótu|Formantu edycji wzbogaconej|Pole kombi rozszerzone|
|Kontrolka listy|Formantu edycji wzbogaconej w wersji 2.0|Kontrolka niestandardowa|

Aby używać wspólnych formantów w oknie dialogowym, należy wywołać [InitCommonControlsEx](/windows/desktop/api/commctrl/nf-commctrl-initcommoncontrolsex) lub `AFXInitCommonControls` przed utworzeniem okna dialogowego.

Aby używać kontrolki RichEdit, należy wywołać `LoadLibrary`. Aby uzyskać więcej informacji, zobacz [o Zaawansowane formanty edycji](/windows/desktop/Controls/about-rich-edit-controls) w zestawie Windows SDK i [Omówienie formantu edycji rozbudowane](../mfc/overview-of-the-rich-edit-control.md).

> [!NOTE]
> Aby używać kontrolki RichEdit z MFC, należy najpierw wywołać [afxinitrichedit2 —](../mfc/reference/application-information-and-management.md#afxinitrichedit2) można załadować kontrolki 2.0 RichEdit (RICHED20. Biblioteka DLL), lub zadzwoń [afxinitrichedit —](../mfc/reference/application-information-and-management.md#afxinitrichedit) załadować starszej kontrolki RichEdit 1.0 (RICHED32. BIBLIOTEKA DLL).
>
> Może używać bieżącego [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) klasy za pomocą starszej kontrolki RichEdit 1.0, ale `CRichEditCtrl` jest przeznaczona wyłącznie do obsługi formantu RichEdit w wersji 2.0. Ponieważ RichEdit 1.0 i RichEdit 2.0 są podobne, większość metod będzie działać. Jednak należy pamiętać, że istnieją pewne różnice między kontrolkami 1.0 i 2.0, więc niektóre metody mogą nie działać prawidłowo lub nie działać w ogóle.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Edytor okien dialogowych](../windows/dialog-editor.md)<br/>
[Kontrolki w oknach dialogowych](controls-in-dialog-boxes.md)<br/>
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