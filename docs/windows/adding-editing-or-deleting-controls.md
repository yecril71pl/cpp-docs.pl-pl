---
title: 'Instrukcje: Dodawanie, edytowanie lub usuwanie kontrolek (C++)'
ms.date: 02/15/2019
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
ms.openlocfilehash: 2e3e671cd92313ad120d2cd6aae3f7e815e09e65
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390987"
---
# <a name="how-to-add-edit-or-delete-controls-c"></a>Instrukcje: Dodawanie, edytowanie lub usuwanie kontrolek (C++)

Za pomocą **Edytor okien dialogowych**, możesz dodać, zmienić rozmiar, edytowanie i usuwanie kontrolki w oknach dialogowych. Można również edytować właściwości kontrolki, takie jak jego identyfikator lub czy jest początkowo widoczne w czasie wykonywania.

**Edytor okien dialogowych** karta jest wyświetlana w [okno przybornika](/visualstudio/ide/reference/toolbox) podczas pracy **Edytor okien dialogowych**. Można również dostosować **przybornika** okna do użytku łatwiejsze. Aby uzyskać więcej informacji, zobacz [korzystanie z przybornika](/visualstudio/ide/using-the-toolbox) i [Pokaż lub Ukryj okno przybornika](showing-or-hiding-the-dialog-editor-toolbar.md).

> [!TIP]
> Podczas korzystania z **Edytor okien dialogowych**, w wielu przypadkach można wybrać przycisk prawym przyciskiem myszy, aby wyświetlić menu skrótów z najczęściej używanymi poleceniami.

## <a name="add-controls"></a>Dodawanie formantów

### <a name="to-add-a-control"></a>Aby dodać kontrolkę

1. Upewnij się, że z kartami okno dialogowe bieżącego dokumentu w ramce edytora. Jeśli okno dialogowe nie jest bieżącym dokumencie, nie będziesz widzieć **Karta Edytor okien dialogowych** w **przybornika**.

1. Na **Edytor okien dialogowych** karcie **przybornika** okna, wybierz formant, a następnie:

   - Wybierz okno dialogowe, w lokalizacji, w którym chcesz umieścić kontrolkę, a ten formant jest widoczny, gdy wybrano.

   - Przeciąganie i upuszczanie formantu z **przybornika** okna do lokalizacji na Twoje okno dialogowe, można przenosić kontrolki lub zmieniać ich rozmiar i kształt.

   - Kliknij dwukrotnie formant w **przybornika** okna i pojawia się na Twoje okno dialogowe, następnie zmienić położenie formantu do lokalizacji, użytkownik sobie tego życzy.

### <a name="to-add-multiple-controls"></a>Aby dodać wiele kontrolek

1. Przytrzymując naciśnięty **Ctrl** klucza, wybierz kontrolkę w **przybornika** okna.

1. Wersja **Ctrl** klucza, a następnie wybierz okno dialogowe dowolną liczbę razy dodać określonego formantu.

1. Naciśnij klawisz **Esc** przestanie umieszczenie kontrolki.

### <a name="to-size-a-control-while-you-add-it"></a>Rozmiar kontrolki podczas dodawania go

1. Wybierz kontrolkę w **przybornika** okna.

1. Umieść kursor wyświetlany na ekranie, którego lewego górnego rogu nowej kontrolki na Twoje okno dialogowe.

1. Wybierz i przytrzymaj naciśnięty przycisk myszy, aby móc zakotwiczyć w lewym górnym rogu formantu w oknie dialogowym, a następnie przeciągnij kursor w prawo i w dół, aż do uzyskania odpowiedni rozmiar kontrolki.

   > [!NOTE]
   > Można zakotwiczyć dowolne dowiedzą o formant, który rysowania. Jako przykład tej procedurze użyto lewego górnego rogu.

1. Zwolnij przycisk myszy. Kontrolka jest gotowy do okna dialogowego w podany rozmiar.

> [!TIP]
> Można zmienić rozmiar formantu po upuszczenie na okno dialogowe, przenosząc uchwytów zmiany rozmiaru w obramowania formantu. Aby uzyskać więcej informacji, zobacz [ustalanie rozmiaru pojedynczych formantów](../windows/sizing-individual-controls.md).

### <a name="to-add-a-custom-control"></a>Aby dodać formant niestandardowy

Można dodać niestandardowe formanty do okna dialogowego wybierając **kontrolki niestandardowej** ikonę **przybornika** i przeciągając je do swojej okna dialogowego. Aby dodać **Syslink** , Dodaj formant niestandardowy, a następnie zmienić formant **klasy** właściwości **Syslink**. Ta akcja spowoduje, że właściwości, aby odświeżyć i Pokaż **Syslink** właściwości formantu. Aby uzyskać informacji na temat klasy otoki MFC, zobacz [CLinkCtrl](../mfc/reference/clinkctrl-class.md).

## <a name="edit-controls"></a>Formanty edycji

### <a name="to-edit-the-properties-of-a-control-or-controls"></a>Edytowanie właściwości kontrolki lub kontrolki

1. W oknie dialogowym Wybierz formant, który chcesz zmodyfikować.

   > [!NOTE]
   > Jeśli wybierzesz wielu formantów, można edytować tylko właściwości wspólne dla wybranych kontrolek.

1. W [okno właściwości](/visualstudio/ide/reference/properties-window), zmień właściwości formantu.

   > [!NOTE]
   > Po ustawieniu **mapy bitowej** właściwości dla przycisku, przycisk radiowy lub kontrolka pola wyboru równa **True**, styl BS_BITMAP został zaimplementowany dla formantu. Aby uzyskać więcej informacji, zobacz [style przycisku](../mfc/reference/styles-used-by-mfc.md#button-styles). Na przykład kojarzenia mapę bitową z kontrolką zobacz [CButton::SetBitmap](../mfc/reference/cbutton-class.md#setbitmap). Mapy bitowe nie będą wyświetlane na kontrolki, gdy jesteś w **Edytor okien dialogowych**.

### <a name="to-undo-changes-to-the-properties-of-a-control"></a>Aby cofnąć zmiany do właściwości kontrolki

1. Upewnij się, że kontrolka ma fokus w **Edytor okien dialogowych**.

1. Przejdź do menu **Edytuj** > **Cofnij**. Jeśli fokus jest na kontrolki, **Cofnij** polecenie jest niedostępne.

### <a name="to-define-a-member-variable-for-a-non-button-dialog-box-control"></a>Aby zdefiniować zmienną składową formantu pola okna dialogowego (inne niż przycisk)

> [!NOTE]
> Ten proces dotyczy tylko kontrolki okna dialogowego, w ramach projektu MFC. Należy używać w projektach ATL **nowych komunikatów Windows do programów obsługi zdarzeń** okno dialogowe. Aby uzyskać więcej informacji, zobacz [komunikat typy związane z obiektami interfejsu użytkownika](../mfc/reference/message-types-associated-with-user-interface-objects.md), [Edytowanie programu obsługi komunikatów](../mfc/reference/editing-a-message-handler.md), i [Definiowanie obsługi komunikatów dla komunikatów odzwierciedlone](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md).

1. W [Edytor okien dialogowych](../windows/dialog-editor.md), wybierz formant.

1. Podczas naciśnięcie **Ctrl** klucza, kliknij dwukrotnie kontrolka okna dialogowego.

   [Kreator dodawania zmiennej składowej](../ide/add-member-variable-wizard.md) pojawia się.

1. Wpisz odpowiednie informacje w **Dodaj zmienną elementu członkowskiego** kreatora. Aby uzyskać więcej informacji, zobacz [wymiana danych okna dialogowego](../mfc/dialog-data-exchange.md).

1. Wybierz **OK** aby powrócić do **Edytor okien dialogowych**.

> [!TIP]
> Aby przejść z dowolnego formantu pola okna dialogowego do jego istniejącej procedury obsługi, kliknij dwukrotnie formant.

Można również użyć **zmienne Członkowskie** karcie [Kreator klas MFC](../mfc/reference/mfc-class-wizard.md) do dodawania nowych zmiennych Członkowskich dla określonej klasy i wyświetlanie zmiennych składowych, które zostały już zdefiniowane.

## <a name="delete-controls"></a>Usuwanie kontrolek

W oknie dialogowym wybierz kontrolkę, naciśnij klawisz **Usuń** klucza lub przejdź do menu **Edytuj** > **Usuń**.

## <a name="other-issues"></a>Inne problemy

### <a name="troubleshooting"></a>Rozwiązywanie problemów

Po dodaniu wspólne kontrolki lub kontrolki edycji wzbogaconej w oknie dialogowym, nie będzie on widoczny podczas testowania okna dialogowego lub się nie pojawi się okno dialogowe, na przykład:

1. Utwórz projekt systemu Win32, modyfikując ustawienia aplikacji, dzięki czemu można utworzyć aplikację Windows (nie Aplikacja konsoli).

1. W [widok zasobów](how-to-create-a-resource-script-file.md#create-resources), kliknij dwukrotnie *.rc* pliku.

1. W obszarze opcji okno dialogowe, kliknij dwukrotnie **o** pole.

1. Dodaj **formant adresu IP** do okna dialogowego.

1. Zapisz i **ponowna kompilacja**.

1. Wykonywanie programu.

1. W oknie dialogowym **pomocy** menu, wybierz opcję **o** polecenie i sprawdź, czy nie pojawia się okno dialogowe.

Obecnie **Edytor okien dialogowych** nie dodaje automatycznie kodu do projektu podczas przeciągania i upuszczania następujące formanty standardowe lub formanty edycji wzbogaconej na okno dialogowe. Ani Visual Studio zapewnia błąd lub ostrzeżenie w przypadku wystąpienia tego problemu. Aby rozwiązać problem, należy ręcznie dodać kodu dla formantu.

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
> Może używać bieżącego [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) klasy za pomocą starszej kontrolki RichEdit 1.0, ale `CRichEditCtrl` jest przeznaczona wyłącznie do obsługi formantu RichEdit w wersji 2.0. Ponieważ RichEdit 1.0 i RichEdit 2.0 są podobne, większość metod będzie działać. Istnieją jednak pewne różnice między kontrolkami 1.0 i 2.0, więc niektóre metody mogą nie działać prawidłowo lub nie działać w ogóle.

### <a name="activex-controls"></a>Kontrolki ActiveX

Program Visual Studio umożliwia wstawianie kontrolki ActiveX z okna dialogowego. Aby uzyskać więcej informacji, zobacz [kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md) i [kontenery kontrolek ActiveX](../mfc/activex-control-containers.md).

**Wstawianie formantu ActiveX** okno dialogowe umożliwia wstawianie kontrolki ActiveX dialogowym podczas korzystania z [Edytor okien dialogowych](../windows/dialog-editor.md). To okno dialogowe zawiera następujące właściwości:

|Właściwość|Opis|
|---|---|
|**ActiveX Control**|Wyświetla listę formantów ActiveX.<br/><br/>Wstawianie kontrolki z tego okna dialogowego nie generuje klasę otoki. Klasa otoki, należy użyć [Widok klas](/visualstudio/ide/viewing-the-structure-of-code) aby go utworzyć, zobacz [Dodawanie klasy](../ide/adding-a-class-visual-cpp.md).<br/><br/>Jeśli formant ActiveX nie pojawia się w tym oknie dialogowym, spróbuj zainstalować kontroli zgodnie z instrukcjami dostawcy.|
|**Path**|Wyświetla plik, w którym znajduje się Kontrolka ActiveX.|

> [!CAUTION]
> Może nie być prawne rozpowszechnianie wszystkich kontrolek ActiveX w Twoim systemie. Zapoznaj się z umową licencyjną dotyczącą oprogramowania, zainstalowanego kontrolki lub skontaktuj się z firmą oprogramowania.

#### <a name="to-add-an-activex-control"></a>Aby dodać formant ActiveX

1. Otwórz okno dialogowe **Edytor okien dialogowych**.

1. Kliknij prawym przyciskiem myszy w dowolnym miejscu w treści okno dialogowe, a następnie wybierz pozycję **Wstawianie formantu ActiveX**.

   **Wstawianie formantu ActiveX** pojawi się okno dialogowe, przedstawiający wszystkie formanty ActiveX w Twoim systemie. W dolnej części okna dialogowego jest wyświetlana ścieżka do pliku formantu ActiveX.

1. Wybierz kontrolkę chcesz dodać do swojej okno dialogowe, a następnie wybierz **OK**.

   Formant ma być wyświetlany w oknie dialogowym, w którym można go edytować lub tworzyć programy obsługi dla niego tak samo, jak dowolną inną kontrolką.

> [!TIP]
> Możesz użyć menu skrótów w **Edytor okien dialogowych** szybkie dodawanie zarejestrowanego kontrolek ActiveX do okna dialogowego lub spróbuj dodać formanty ActiveX do **przybornika** okna, aby mieć łatwy dostęp.

#### <a name="to-edit-properties-for-an-activex-control"></a>Aby edytować właściwości kontrolki ActiveX

Kontrolki ActiveX, dostarczone przez niezależnych dostawców może są wyposażone w ich własnych właściwości i właściwości. Te właściwości są wyświetlane w **właściwości** okna, włącznie z dowolnej właściwości strony utworzone przez autorów formantu ActiveX są wyświetlane w **strony właściwości** okno dialogowe (w celu wyświetlania  **Strona właściwości** określonej kontrolki ActiveX, wybierz **strona właściwości** znajdujący się w [okno właściwości](/visualstudio/ide/reference/properties-window)).

- Wybierz **ActiveX** kontroli i przejdź do menu **widoku** > **strona właściwości** Aby wyświetlić właściwości. W razie potrzeby na stronie właściwości, należy wprowadzić zmiany.

   Na stronie właściwości dla formantu ActiveX, w zależności od arkuszy właściwości, które pochodzą z formantu ActiveX w ramach będą wyświetlane różne karty.

> [!NOTE]
> Ta procedura ma zastosowanie przy użyciu strony właściwości, aby edytować kontrolki ActiveX. Możesz również przeglądać i edytować właściwości formantu ActiveX w nowym **właściwości** okna.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Zarządzanie formantów okna dialogowego](controls-in-dialog-boxes.md)<br/>
[Instrukcje: Kontrolki układu](arrangement-of-controls-on-dialog-boxes.md)<br/>
[Instrukcje: Definiowanie dostępu do kontrolek i ich wartości](defining-mnemonics-access-keys.md)<br/>

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