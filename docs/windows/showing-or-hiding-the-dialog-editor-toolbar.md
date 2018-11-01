---
title: Pokazywanie lub ukrywanie paska narzędzi edytora okien dialogowych (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], showing or hiding Dialog editor toolbar
- toolbars [C++], showing
- toolbars [C++], hiding
- Dialog Editor [C++], showing or hiding toolbar
ms.assetid: 93c255e1-90eb-48b6-8602-450acda75bed
ms.openlocfilehash: e025f560a47f85d17b8c56a4db19f322069d33ef
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631091"
---
# <a name="showing-or-hiding-the-dialog-editor-toolbar-c"></a>Pokazywanie lub ukrywanie paska narzędzi edytora okien dialogowych (C++)

Po otwarciu **okna dialogowego** edytora w projekcie w języku C++ **Edytor okien dialogowych** pasek narzędzi pojawia się automatycznie w górnej części rozwiązania.

### <a name="dialog-editor-toolbar"></a>Pasek narzędzi edytora okien dialogowych

|Ikona|Znaczenie|Ikona|Znaczenie|
|----------|-------------|----------|-------------|
|![Przycisk okna dialogowego test](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|Okno dialogowe testu|![Miejsce na przycisku](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|Między|
|![Przycisk wej wyrównania](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|Wyrównaj wej|![Przycisk miejsce w dół](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|W dół|
|![Przycisk praw wyrównania](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|Wyrównaj prawa|![Przycisk tej samej szerokości upewnij](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|Taka sama szerokość|
|![Wyrównaj górne krawędzie przycisk](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|Wyrównaj górne krawędzie|![Marka sama wysokość przycisku](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|Taka sama wysokość|
|![Wyrównaj do dołu przycisk](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|Wyrównaj do dołu|![Utwórz ten sam rozmiar przycisku](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|Taki sam rozmiar|
|![Środkowy przycisk pionowe](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|W pionie|![Przełącz przycisk siatki](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|Przełączanie siatki|
|![Środkowy przycisk poziomy](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|Poziome|![Przełącz prowadnice przycisk](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|Przełącz prowadnice|

**Edytor okien dialogowych** narzędzi zawiera przyciski rozmieszczanie układu kontrolek w oknie dialogowym, na przykład rozmiar i wyrównanie. **Edytor okien dialogowych** przycisków paska narzędzi odpowiadają poleceń na **Format** menu. Aby uzyskać więcej informacji, zobacz [klucze akceleratora dla edytora okien dialogowych](../windows/accelerator-keys-for-the-dialog-editor.md).

Podczas pracy w **okna dialogowego** edytora, można przełączać wyświetlanie **Edytor okien dialogowych** narzędzi, wybierając je z listy dostępnych pasków narzędzi i okien.

### <a name="to-show-or-hide-the-dialog-editor-toolbar"></a>Aby pokazać lub ukryć pasek narzędzi edytora okna dialogowego

1. Na **widoku** kliknij menu **pasków narzędzi** wybierz **Edytor okien dialogowych** z podmenu.

   > [!NOTE]
   > **Edytor okien dialogowych** pasek narzędzi jest wyświetlany domyślnie po otwarciu okna dialogowego pole zasobu w edytorze okien dialogowych; jednak jeśli pasek narzędzi jest jawnie zamknięty, należy wywołać ją przy następnym otwarciu zasobów okno dialogowe.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Rozmieszczenie kontrolek w oknach dialogowych](../windows/arrangement-of-controls-on-dialog-boxes.md)<br/>
[Instrukcje: tworzenie zasobu](../windows/how-to-create-a-resource.md)<br/>
[Pliki zasobów](../windows/resource-files-visual-studio.md)<br/>
[Edytor okien dialogowych](../windows/dialog-editor.md)