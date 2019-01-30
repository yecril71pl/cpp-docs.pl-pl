---
title: Dodawanie kontrolki do okna dialogowego (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog.dialog
helpviewer_keywords:
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
ms.assetid: b2a26d19-093f-49ca-93da-fef00dfbb381
ms.openlocfilehash: 92b644769bcbe2649d00ba68437bd474ee06dfcc
ms.sourcegitcommit: b488462a6e035131121e6f32d8f3b108cc798b5e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55293627"
---
# <a name="adding-a-control-to-a-dialog-box-c"></a>Dodawanie kontrolki do okna dialogowego (C++)

**Edytor okien dialogowych** karta jest wyświetlana w [okno przybornika](/visualstudio/ide/reference/toolbox) podczas pracy **okna dialogowego** edytora. Aby dodać formanty do Twojego nowego okna dialogowego, przeciągnij formanty z **przybornika** do okna dialogowego, który tworzysz. Możesz przenosić kontrolki lub zmieniać ich rozmiar i kształt.

Formanty standardowe dostępne w **przybornika** są:

- [Kontrolka przycisku](../mfc/reference/cbutton-class.md)

- [Kontrolka pola wyboru](../mfc/reference/styles-used-by-mfc.md#button-styles)

- [Kontrolka pola kombi](../mfc/reference/ccombobox-class.md)

- [Edytuj kontrolkę](../mfc/reference/cedit-class.md)

- Pole grupy

- [Kontrolka pola listy](../mfc/reference/clistbox-class.md)

- [Kontrolka przycisku radiowego](../mfc/reference/styles-used-by-mfc.md#button-styles)

- [Kontrolka tekstu statycznego](../mfc/reference/cstatic-class.md)

- [Formant obrazu](../mfc/reference/cpictureholder-class.md)

- [Kontrolka 2.0 edycji wzbogaconej](../mfc/using-cricheditctrl.md)

- [Pasek przewijania](../mfc/reference/cscrollbar-class.md)

[Wspólnych formantów Windows](../mfc/controls-mfc.md) dostępne w **przybornika** zapewniają większą funkcjonalność w aplikacji. Obejmują one:

- [Kontrolka suwaka](../mfc/slider-control-styles.md)

- [Kontrolki pokrętła](../mfc/using-cspinbuttonctrl.md)

- [Kontrolki postępu](../mfc/styles-for-the-progress-control.md)

- [Formantu klawisza dostępu](../mfc/using-a-hot-key-control.md)

- [Kontrolka listy](../mfc/list-control-and-list-view.md)

- [Kontrolka drzewa](../mfc/tree-control-styles.md)

- [Kontrolki karty](../mfc/tab-controls-and-property-sheets.md)

- [Kontrolki animacji](../mfc/using-an-animation-control.md)

- [Kontrolka czasu selektora daty](../mfc/creating-the-date-and-time-picker-control.md)

- [Kontrolowanie kalendarza miesięcznego](../mfc/month-calendar-control-examples.md)

- [Formant adresu IP](../mfc/reference/cipaddressctrl-class.md)

- [Rozszerzone formant pola kombi](../mfc/creating-an-extended-combo-box-control.md)

- [Kontrolka niestandardowa](custom-controls-in-the-dialog-editor.md)

Można dodać niestandardowe formanty do okna dialogowego wybierając **kontrolki niestandardowej** ikonę **przybornika** i przeciągając je do swojej okna dialogowego. Aby dodać **Syslink** , Dodaj formant niestandardowy, a następnie zmienić formant **klasy** właściwości **Syslink**. Spowoduje to właściwości, aby odświeżyć i Pokaż **Syslink** właściwości formantu. Aby uzyskać informacji na temat klasy otoki MFC, zobacz [CLinkCtrl](../mfc/reference/clinkctrl-class.md).

Możesz również [Dodawanie kontrolek ActiveX do dialogowym](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).

Można również dostosować **przybornika** okna do użytku łatwiejsze. Aby uzyskać więcej informacji, zobacz [korzystanie z przybornika](/visualstudio/ide/using-the-toolbox).

Aby uzyskać więcej informacji na temat korzystania z **RichEdit 1.0** kontrolką MFC, zobacz [używanie formantu RichEdit 1.0 z MFC](../windows/using-the-richedit-1-0-control-with-mfc.md)

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-add-a-control-to-a-dialog-box"></a>Aby dodać formant do okna dialogowego

1. Upewnij się, że z kartami okno dialogowe bieżącego dokumentu w ramce edytora. Jeśli okno dialogowe nie jest bieżącym dokumencie, nie będziesz widzieć **Karta Edytor okien dialogowych** w **przybornika**.

1. Na **Edytor okien dialogowych** karcie [okno przybornika](/visualstudio/ide/reference/toolbox), wybierz kontrolkę, należy następnie:

   - Wybierz okno dialogowe, w lokalizacji, w którym chcesz umieścić formant. Ten formant jest widoczny, gdy wybrano.

       \- lub —

   - Przeciąganie i upuszczanie formantu z **przybornika** okna do lokalizacji na Twoje okno dialogowe.

       \- lub —

   - Kliknij dwukrotnie formant w **przybornika** okna (jest wyświetlana na dialogowym), a następnie zmiana położenia kontrolki do lokalizacji, użytkownik sobie tego życzy.

## <a name="to-add-multiple-controls"></a>Aby dodać wiele kontrolek

1. Przytrzymując naciśnięty **Ctrl** klucza, wybierz kontrolkę w [okno przybornika](/visualstudio/ide/reference/toolbox).

1. Wersja **Ctrl** klucza, a następnie wybierz okno dialogowe dowolną liczbę razy dodać określonego formantu.

1. Naciśnij klawisz **Esc** przestanie umieszczenie kontrolki.

## <a name="to-size-a-control-while-you-add-it"></a>Rozmiar kontrolki podczas dodawania go

1. Wybierz kontrolkę w [okno przybornika](/visualstudio/ide/reference/toolbox).

1. Umieść kursor w miejscu (która jest wyświetlana jako krzyżowe na ekranie), w której chcesz lewego górnego rogu nowej kontrolki na Twoje okno dialogowe.

1. Wybierz i przytrzymaj naciśnięty przycisk myszy, aby móc zakotwiczyć w lewym górnym rogu formantu w oknie dialogowym, a następnie przeciągnij kursor w prawo i w dół, aż do uzyskania odpowiedni rozmiar kontrolki.

   > [!NOTE]
   > Faktycznie można zakotwiczyć dowolne dowiedzą o formant, który rysowania. Jako przykład tej procedurze użyto lewego górnego rogu.

1. Zwolnij przycisk myszy. Kontrolka jest gotowy do okna dialogowego w podany rozmiar.

   > [!TIP]
   > Można zmienić rozmiar formantu po upuszczenie na okno dialogowe, przenosząc uchwytów zmiany rozmiaru w obramowania formantu. Aby uzyskać więcej informacji, zobacz [ustalanie rozmiaru pojedynczych formantów](../windows/sizing-individual-controls.md).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)<br/>
[Dodawanie obsługi zdarzeń dla kontrolek okna dialogowego](../windows/adding-event-handlers-for-dialog-box-controls.md)<br/>
[Kontrolki okna dialogowego i typy zmiennych](../ide/dialog-box-controls-and-variable-types.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)<br/>
[Klasy kontrolek](../mfc/control-classes.md)<br/>
[Klasy okien dialogowych](../mfc/dialog-box-classes.md)<br/>
[Style paska przewijania](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles)<br/>
[Przykłady kontrolek edycji wzbogaconej](../mfc/rich-edit-control-examples.md)<br/>
