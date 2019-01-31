---
title: Rozwiązywanie problemów z edytorem okien dialogowych (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], troubleshooting
- Dialog Editor [C++], troubleshooting
- dialog boxes [C++], troubleshooting
- InitCommonControls
- RichEdit 1.0 control
- rich edit controls [C++], RichEdit 1.0
ms.assetid: 21882868-5ac4-4a41-a4a6-eaaa059402ea
ms.openlocfilehash: fe0fe704b5c17d0db4e3419f29d21f0e60bc4211
ms.sourcegitcommit: 5270117dbecc4c49bca0cf10b927bae3c9930038
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484958"
---
# <a name="troubleshooting-the-dialog-editor-c"></a>Rozwiązywanie problemów z edytorem okien dialogowych (C++)

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

Poniżej przedstawiono kilka kwestii, o których należy pamiętać, pracując w języku C++ **okna dialogowego** Edytor:

## <a name="adding-controls-to-a-dialog-causes-the-dialog-to-no-longer-function"></a>Dodawanie formantów do okna dialogowego powoduje, że okno dialogowe, aby nie jest już — funkcja

Po dodaniu wspólne kontrolki lub kontrolki edycji wzbogaconej w oknie dialogowym, nie będzie on widoczny podczas testowania okna dialogowego lub nie będzie wyświetlane okno dialogowe, sam.

### <a name="example-of-the-problem"></a>Przykład problemu

1. Utwórz projekt systemu Win32, modyfikując ustawienia aplikacji, dzięki czemu można utworzyć aplikację Windows (nie Aplikacja konsoli).

1. W [widok zasobów](../windows/resource-view-window.md), kliknij dwukrotnie plik .rc.

1. W obszarze opcji okno dialogowe, kliknij dwukrotnie **o** pole.

1. Dodaj **formant adresu IP** do okna dialogowego.

1. Zapisz i **ponowna kompilacja**.

1. Wykonywanie programu.

1. W oknie dialogowym **pomocy** menu, kliknij przycisk **o** polecenia; nie okno dialogowe zostanie wyświetlone okno.

### <a name="the-cause"></a>Przyczyny

Obecnie **okna dialogowego** edytora nie dodaje automatycznie kodu do projektu podczas przeciągania i upuszczania następujące formanty standardowe lub formanty edycji wzbogaconej na okno dialogowe. Ani Visual Studio zapewnia błąd lub ostrzeżenie w przypadku wystąpienia tego problemu. Aby rozwiązać problem, należy ręcznie dodać kodu dla formantu.

||||
|-|-|-|
|Kontrolka suwaka|Kontrolka drzewa|Wybór daty i godziny|
|Kontrolki pokrętła|Kontrolki karty|Kalendarza miesięcznego|
|Kontrolki postępu|Kontrolki animacji|Formant adresu IP|
|Klawisz skrótu|Formantu edycji wzbogaconej|Pole kombi rozszerzone|
|Kontrolka listy|Formantu edycji wzbogaconej w wersji 2.0|Kontrolka niestandardowa|

### <a name="fix-for-common-controls"></a>Poprawka dla formantów standardowych

Aby używać wspólnych formantów w oknie dialogowym, należy wywołać [InitCommonControlsEx](/windows/desktop/api/commctrl/nf-commctrl-initcommoncontrolsex) lub `AFXInitCommonControls` przed utworzeniem okna dialogowego.

### <a name="fix-for-richedit-controls"></a>Poprawka dla kontrolki RichEdit

Należy wywołać `LoadLibrary` dla formantów edycji. Aby uzyskać więcej informacji, zobacz [o Zaawansowane formanty edycji](/windows/desktop/Controls/about-rich-edit-controls) w zestawie Windows SDK i [Omówienie formantu edycji rozbudowane](../mfc/overview-of-the-rich-edit-control.md).

### <a name="requirements"></a>Wymagania

Win32

## <a name="using-the-richedit-10-control-with-mfc"></a>Używanie formantu RichEdit 1.0 z MFC

Aby użyć kontrolki RichEdit, najpierw musisz wywołać [afxinitrichedit2 —](../mfc/reference/application-information-and-management.md#afxinitrichedit2) można załadować kontrolki 2.0 RichEdit (RICHED20. Biblioteka DLL), lub zadzwoń [afxinitrichedit —](../mfc/reference/application-information-and-management.md#afxinitrichedit) załadować starszej kontrolki RichEdit 1.0 (RICHED32. BIBLIOTEKA DLL).

Może używać bieżącego [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) klasy za pomocą starszej kontrolki RichEdit 1.0, ale `CRichEditCtrl` jest przeznaczona wyłącznie do obsługi formantu RichEdit w wersji 2.0. Ponieważ RichEdit 1.0 i RichEdit 2.0 są podobne, większość metod będzie działać. Jednak należy pamiętać, że istnieją pewne różnice między kontrolkami 1.0 i 2.0, więc niektóre metody mogą nie działać prawidłowo lub nie działać w ogóle.

### <a name="requirements"></a>Wymagania

MFC

## <a name="see-also"></a>Zobacz też

[Edytor okien dialogowych](../windows/dialog-editor.md)