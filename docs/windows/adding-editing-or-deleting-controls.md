---
title: 'Instrukcje: Dodawanie, edytowanie lub usuwanie kontrolek (C++)'
ms.date: 02/15/2019
f1_keywords:
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
ms.openlocfilehash: ad14a0500336bc1ca61e00bcd6d9a6e1088afc81
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167527"
---
# <a name="how-to-add-edit-or-delete-controls-c"></a>Instrukcje: Dodawanie, edytowanie lub usuwanie kontrolek (C++)

Za pomocą **edytora okien**dialogowych można dodawać kontrolki, zmieniać ich rozmiar, edytować i usuwać w oknach dialogowych. Możesz również edytować właściwości kontrolki, takie jak jej identyfikator, lub czy początkowo jest ona widoczna w czasie wykonywania.

Gdy Pracujesz w **edytorze okien dialogowych**, w [oknie przybornika](/visualstudio/ide/reference/toolbox) zostanie wyświetlona karta **Edytor okien dialogowych** . Możesz również dostosować okno **przybornika** , aby ułatwić korzystanie z niego. Aby uzyskać więcej informacji, zobacz [Korzystanie z przybornika](/visualstudio/ide/using-the-toolbox) i [Pokaż lub Ukryj okno przybornika](showing-or-hiding-the-dialog-editor-toolbar.md).

> [!TIP]
> Korzystając z **edytora okien dialogowych**, w wielu przypadkach można wybrać prawy przycisk myszy, aby wyświetlić menu skrótów często używanych poleceń.

## <a name="add-controls"></a>Dodawanie kontrolek

### <a name="to-add-a-control"></a>Aby dodać kontrolkę

1. Upewnij się, że okno dialogowe z kartami jest bieżącym dokumentem w ramce edytora. Jeśli okno dialogowe nie jest bieżącym dokumentem, **karta Edytor okien dialogowych** nie zostanie wyświetlona w **przyborniku**.

1. Na karcie **Edytor okna dialogowego** okna **przybornika** wybierz żądaną kontrolkę, a następnie:

   - Zaznacz okno dialogowe w lokalizacji, w której chcesz umieścić formant, a kontrolka pojawia się, gdy została wybrana.

   - Przeciągnij i upuść formant z okna **przybornika** do lokalizacji w oknie dialogowym. Następnie można przenieść kontrolkę dookoła lub zmienić jej rozmiar i kształt.

   - Kliknij dwukrotnie formant w oknie **przybornika** i pojawi się on w oknie dialogowym. Zmień położenie kontrolki na preferowaną lokalizację.

### <a name="to-add-multiple-controls"></a>Aby dodać wiele kontrolek

1. Przytrzymując wciśnięty klawisz **Ctrl** , w oknie **przybornika** zaznacz kontrolkę.

1. Zwolnij klawisz **Ctrl** i wybierz okno dialogowe tyle razy, ile chcesz dodać określoną kontrolkę.

1. Naciśnij klawisz **ESC** , aby zatrzymać umieszczanie kontrolek.

### <a name="to-size-a-control-while-you-add-it"></a>Aby zmienić rozmiar kontrolki podczas dodawania

1. Wybierz kontrolkę w oknie **Przybornik** .

1. Umieść kursor, który pojawia się jako krzyżyk celownika, gdzie chcesz, aby w lewym górnym rogu nowej kontrolki znajdować się w oknie dialogowym.

1. Wybierz i przytrzymaj przycisk myszy, aby zakotwiczyć lewy górny róg kontrolki w oknie dialogowym. Następnie przeciągnij kursor w prawo i w dół, aż formant będzie miał żądany rozmiar.

   > [!NOTE]
   > Można zakotwiczyć dowolny z czterech rogów kontrolki, która jest na rysunku. Ta procedura służy jako przykład w lewym górnym rogu.

1. Zwolnij przycisk myszy. Kontrolka jest rozliczana w oknie dialogowym o określonym rozmiarze.

> [!TIP]
> Można zmienić rozmiar kontrolki po porzucenie jej do okna dialogowego, przenosząc uchwyty rozmiaru na granicy formantu. Aby uzyskać więcej informacji, zobacz [ustalanie rozmiarów poszczególnych kontrolek](../windows/sizing-individual-controls.md).

### <a name="to-add-a-custom-control"></a>Aby dodać kontrolkę niestandardową

Możesz dodać niestandardowe kontrolki do okna dialogowego. Wybierz ikonę **kontrolki niestandardowej** w **przyborniku** i przeciągnij ją do okna dialogowego. Aby dodać kontrolkę `Syslink`, Dodaj kontrolkę niestandardową, a następnie zmień właściwość **klasy** kontrolki na `Syslink`. Ta akcja spowoduje odświeżenie właściwości i wyświetlenie właściwości kontrolki `Syslink`. Aby uzyskać informacje na temat klasy otoki MFC, zobacz [CLinkCtrl](../mfc/reference/clinkctrl-class.md).

## <a name="edit-controls"></a>Edytuj kontrolki

### <a name="to-edit-the-properties-of-a-control-or-controls"></a>Aby edytować właściwości kontrolki lub kontrolek

1. W oknie dialogowym Wybierz kontrolkę, którą chcesz zmodyfikować.

   > [!NOTE]
   > W przypadku wybrania wielu formantów można edytować tylko właściwości wspólne dla wybranych kontrolek.

1. W [okno właściwości](/visualstudio/ide/reference/properties-window)Zmień właściwości formantu.

   > [!NOTE]
   > Po ustawieniu właściwości **Mapa bitowa** przycisku, przycisku radiowego lub kontrolki pola wyboru równej **true**, BS_BITMAP stylu jest zaimplementowana dla kontrolki. Aby uzyskać więcej informacji, zobacz [style przycisków](../mfc/reference/styles-used-by-mfc.md#button-styles). Aby zapoznać się z przykładem kojarzenia mapy bitowej z kontrolką, zobacz [CButton:: Setmapa bitowa](../mfc/reference/cbutton-class.md#setbitmap). Mapy bitowe nie będą wyświetlane w kontrolce, gdy jesteś w **edytorze okien dialogowych**.

### <a name="to-undo-changes-to-the-properties-of-a-control"></a>Aby cofnąć zmiany właściwości kontrolki

1. Upewnij się, że kontrolka ma fokus w **edytorze okien dialogowych**.

1. Przejdź do menu **edytuj** > **Cofnij**. Jeśli fokus nie znajduje się na kontrolce, polecenie **Cofnij** będzie niedostępne.

### <a name="to-define-a-member-variable-for-a-non-button-dialog-box-control"></a>Aby zdefiniować zmienną członkowską dla kontrolki okna dialogowego (niebędącej przyciskiem)

> [!NOTE]
> Ten proces dotyczy tylko formantów okna dialogowego w projekcie MFC. Projekty ATL powinny używać okna dialogowego **nowe komunikaty systemu Windows i obsługi zdarzeń** . Aby uzyskać więcej informacji, zobacz [typy komunikatów skojarzonych z obiektami interfejsu użytkownika](../mfc/reference/message-types-associated-with-user-interface-objects.md), [Edytowanie programu obsługi komunikatów](../mfc/reference/editing-a-message-handler.md)i [Definiowanie obsługi komunikatów dla wiadomości odbitej](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md).

1. W [edytorze okien dialogowych](../windows/dialog-editor.md)Wybierz kontrolkę.

1. Podczas naciskania klawisza **Ctrl** kliknij dwukrotnie formant okna dialogowego.

   Zostanie wyświetlony [Kreator dodawania zmiennej członkowskiej](../ide/add-member-variable-wizard.md) .

1. Wpisz odpowiednie informacje w kreatorze **dodawania zmiennej członkowskiej** . Aby uzyskać więcej informacji, zobacz [wymiana danych w oknie dialogowym](../mfc/dialog-data-exchange.md).

1. Wybierz **przycisk OK** , aby powrócić do **edytora okien dialogowych**.

> [!TIP]
> Aby przejść z dowolnego formantu okna dialogowego do jego istniejącej procedury obsługi, kliknij dwukrotnie formant.

Możesz również użyć karty **zmienne składowe** w [Kreatorze klas MFC](../mfc/reference/mfc-class-wizard.md) , aby dodać nowe zmienne Członkowskie dla określonej klasy i wyświetlić już zdefiniowane Zmienne Członkowskie.

## <a name="delete-controls"></a>Usuń kontrolki

W oknie dialogowym Wybierz kontrolkę, a następnie naciśnij klawisz **delete** lub przejdź do menu **Edytuj** > **Usuń**.

## <a name="other-issues"></a>Inne problemy

### <a name="troubleshooting"></a>Rozwiązywanie problemów

Po dodaniu kontrolki formant wspólny lub edycji wzbogaconej do okna dialogowego nie będzie on wyświetlany podczas testowania okna dialogowego. Lub samo okno dialogowe nie zostanie wyświetlone. Na przykład:

1. Utwórz projekt Win32, modyfikując ustawienia aplikacji, aby utworzyć aplikację systemu Windows (nie aplikację konsolową).

1. W [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources)kliknij dwukrotnie plik *. RC* .

1. W oknie dialogowym kliknij dwukrotnie pole **informacje** .

1. Dodaj **kontrolkę adres IP** do okna dialogowego.

1. Zapisz i **Skompiluj ponownie wszystko**.

1. Wykonaj program.

1. W menu **Pomoc** okna dialogowego wybierz polecenie **informacje** i nie wyświetlaj okna dialogowego.

Obecnie **Edytor okien dialogowych** nie dodaje automatycznie kodu do projektu podczas przeciągania i upuszczania następujących formantów standardowych lub kontrolek edycji wzbogaconej do okna dialogowego. Program Visual Studio nie udostępnia błędu ani Ostrzeżenia w przypadku wystąpienia tego problemu. Aby rozwiązać ten problem, należy ręcznie dodać kod dla kontrolki.

||||
|-|-|-|
|Kontrolka suwaka|Kontrolka drzewa|Wybór daty i godziny|
|Kontrolka pokrętła|Kontrolka karta|Kalendarz miesięczny|
|Kontrolka postępu|Kontrolka animacji|Kontrola adresów IP|
|Klawisz dostępu|Kontrolka edycji wzbogaconej|Rozszerzone pole kombi|
|Kontrolka listy|Kontrolka edycji wzbogaconej 2,0|Kontrolka niestandardowa|

Aby użyć formantów wspólnych w oknie dialogowym, należy wywołać [Funkcja InitCommonControlsEx](/windows/win32/api/commctrl/nf-commctrl-initcommoncontrolsex) lub `AFXInitCommonControls` przed utworzeniem okna dialogowego.

Aby użyć formantów RichEdit, należy wywołać `LoadLibrary`. Aby uzyskać więcej informacji, zobacz [Informacje o kontrolkach edycji wzbogaconej](/windows/win32/Controls/about-rich-edit-controls) w Windows SDK i [Omówienie kontrolki edycji wzbogaconej](../mfc/overview-of-the-rich-edit-control.md).

> [!NOTE]
> Aby użyć formantu RichEdit z MFC, należy najpierw wywołać [Funkcja afxinitrichedit2](../mfc/reference/application-information-and-management.md#afxinitrichedit2) , aby załadować formant RichEdit 2,0 (biblioteki riched20. DLL) lub Call [AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit) w celu załadowania starszej kontrolki RichEdit 1,0 (Riched32. DLL).
>
> Można użyć bieżącej klasy [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) z starszą kontrolką RichEdit 1,0, ale `CRichEditCtrl` jest przeznaczona tylko do obsługi formantu RichEdit 2,0. Ponieważ RichEdit 1,0 i RichEdit 2,0 są podobne, większość metod będzie działała. Istnieją jednak pewne różnice między kontrolkami 1,0 i 2,0, dlatego niektóre metody mogą funkcjonować nieprawidłowo lub nie działały wcale.

### <a name="activex-controls"></a>Kontrolki ActiveX

Program Visual Studio umożliwia Wstawianie kontrolek ActiveX do okna dialogowego. Aby uzyskać więcej informacji, zobacz [kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md) i [kontenery kontrolek ActiveX](../mfc/activex-control-containers.md).

Okno dialogowe **Wstawianie kontrolki ActiveX** umożliwia Wstawianie kontrolek ActiveX do okna dialogowego podczas korzystania z [edytora okien dialogowych](../windows/dialog-editor.md). To okno dialogowe zawiera następujące właściwości:

|Właściwość|Opis|
|---|---|
|**Kontrolka ActiveX**|Wyświetla listę kontrolek ActiveX.<br/><br/>Wstawianie kontrolki z tego okna dialogowego nie powoduje wygenerowania klasy otoki. Jeśli potrzebujesz klasy otoki, użyj [Widok klasy](/visualstudio/ide/viewing-the-structure-of-code) , aby ją utworzyć, zobacz [Dodawanie klasy](../ide/adding-a-class-visual-cpp.md).<br/><br/>Jeśli formant ActiveX nie jest wyświetlany w tym oknie dialogowym, spróbuj zainstalować formant zgodnie z instrukcjami dostawcy.|
|**Ścieżka**|Wyświetla plik, w którym znajduje się kontrolka ActiveX.|

> [!CAUTION]
> Dystrybucja wszystkich formantów ActiveX w systemie może nie być poprawna. Zapoznaj się z umową licencyjną dotyczącą oprogramowania, które zainstalowało kontrolki, lub skontaktuj się z firmą oprogramowania.

#### <a name="to-add-an-activex-control"></a>Aby dodać kontrolkę ActiveX

1. Otwórz okno dialogowe w **edytorze okien dialogowych**.

1. Kliknij prawym przyciskiem myszy w dowolnym miejscu w treści okna dialogowego i wybierz polecenie **Wstaw kontrolkę ActiveX**.

   Zostanie wyświetlone okno dialogowe **Wstawianie kontrolki ActiveX** zawierające wszystkie kontrolki ActiveX w systemie. W dolnej części okna dialogowego pojawia się ścieżka do pliku kontrolki ActiveX.

1. Wybierz kontrolkę, którą chcesz dodać do okna dialogowego, a następnie wybierz **przycisk OK**.

   Kontrolka pojawia się w oknie dialogowym, w którym można ją edytować lub tworzyć programy obsługi w taki sam sposób jak każdy inny formant.

> [!TIP]
> Możesz użyć menu skrótów w **edytorze okien dialogowych** , aby szybko dodać zarejestrowane kontrolki ActiveX do okna dialogowego, lub spróbować dodać kontrolki ActiveX w oknie **przybornika** , aby uzyskać łatwy dostęp.

#### <a name="to-edit-properties-for-an-activex-control"></a>Aby edytować właściwości kontrolki ActiveX

Kontrolki ActiveX dostarczone przez niezależnych dostawców mogą mieć własne właściwości i cechy. Te właściwości są wyświetlane w oknie **Właściwości** . Wszystkie strony właściwości utworzone przez autorów kontrolki ActiveX są wyświetlane w oknie dialogowym **właściwości strony** . (Aby wyświetlić **stronę właściwości** dla konkretnej kontrolki ActiveX, wybierz przycisk **strony właściwości** w [okno właściwości](/visualstudio/ide/reference/properties-window)).

- Wybierz kontrolkę **ActiveX** i przejdź do **widoku** menu > **stronie właściwości** , aby wyświetlić właściwości. Wprowadź odpowiednie zmiany na stronie właściwości.

   Na stronie właściwości kontrolki ActiveX są wyświetlane różne karty, w zależności od arkuszy właściwości, które są częścią kontrolki ActiveX.

> [!NOTE]
> Ta procedura ma zastosowanie do edycji kontrolek ActiveX przy użyciu strony właściwości. Możesz również przeglądać i edytować właściwości ActiveX w oknie nowe **Właściwości** .

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Zarządzanie kontrolkami okien dialogowych](controls-in-dialog-boxes.md)<br/>
[Instrukcje: kontrolki układu](arrangement-of-controls-on-dialog-boxes.md)<br/>
[Instrukcje: definiowanie dostępu i wartości kontroli](defining-mnemonics-access-keys.md)

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
