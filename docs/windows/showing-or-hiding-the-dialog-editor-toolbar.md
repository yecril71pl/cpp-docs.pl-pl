---
title: "Pokazywanie lub ukrywanie paska narzędzi edytora okien dialogowych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], showing or hiding Dialog editor toolbar
- toolbars [C++], showing
- toolbars [C++], hiding
- Dialog editor, showing or hiding toolbar
ms.assetid: 93c255e1-90eb-48b6-8602-450acda75bed
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dbb77c6851b9e8b93c1b3bbd0b1d30bcf65e3d42
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="showing-or-hiding-the-dialog-editor-toolbar"></a>Pokazywanie i ukrywanie paska narzędzi Edytora okien dialogowych
Po otwarciu edytora okien dialogowych paska narzędzi edytora okien dialogowych automatycznie pojawia się w górnej części rozwiązania.  
  
### <a name="dialog-editor-toolbar"></a>Pasek narzędzi edytora okien dialogowych  
  
|Ikona|Znaczenie|Ikona|Znaczenie|  
|----------|-------------|----------|-------------|  
|![Przycisk Testuj okno dialogowe](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|Okno dialogowe testu|![Miejsce na przycisku](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|Między|  
|![Dopasuj przycisk wej](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|Wyrównywanie lewych krawędzi|![Przycisk miejsce w dół](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|W dół|  
|![Dopasuj przycisk prawa](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|Dopasuj prawa|![Przycisk tej samej szerokości upewnij](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|Taka sama szerokość|  
|![Dopasuj górne przycisk](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|Dopasuj górne|![Przycisk wysokością upewnij](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|Wysokość tego samego|  
|![Wyrównaj do dołu przycisk](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|Wyrównaj do dołu|![Utwórz sam rozmiar przycisku](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|Jednakowe wymiary|  
|![Środkowy przycisk pionowy](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|Pionowe|![Przycisk przełączania siatki](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|Przełączanie siatki|  
|![Środkowy przycisk poziomy](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|poziomy|![Przycisk przełączania przewodniki](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|Przewodniki przełączania|  
  
 Na pasku narzędzi edytora okien dialogowych zawiera przyciski rozmieszczanie formantów w oknie dialogowym, na przykład rozmiar i wyrównanie układu. Przyciski paska narzędzi edytora okien dialogowych odpowiadają polecenia w Format menu. Aby uzyskać więcej informacji, zobacz [klucze akceleratora dla edytora okien dialogowych](../windows/accelerator-keys-for-the-dialog-editor.md).  
  
 Podczas pracy w edytorze okien dialogowych, wybierając ją z listy dostępnych pasków narzędzi i systemu windows można przełączyć wyświetlania paska narzędzi edytora okien dialogowych.  
  
### <a name="to-show-or-hide-the-dialog-editor-toolbar"></a>Aby wyświetlić lub ukryć pasek narzędzi edytora okna dialogowego  
  
1.  Na **widoku** kliknij menu **paski narzędzi** wybierz **Edytor okien dialogowych** z podmenu.  
  
    > [!NOTE]
    >  Po otwarciu zasobów okno dialogowe w edytorze okien dialogowych; domyślnie jest wyświetlana na pasku narzędzi edytora okien dialogowych Jednak jeśli zamkniesz jawnie pasek narzędzi, należy go wywołać przy następnym otwarciu zasobów okno dialogowe.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Wymagania  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Rozmieszczenie formantów w oknach dialogowych](../windows/arrangement-of-controls-on-dialog-boxes.md)   
 [Porady: tworzenie zasobu](../windows/how-to-create-a-resource.md)   
 [Pliki zasobów](../windows/resource-files-visual-studio.md)   
 [Edytor okien dialogowych](../windows/dialog-editor.md)

