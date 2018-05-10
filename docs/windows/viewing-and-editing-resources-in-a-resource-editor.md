---
title: Wyświetlanie i edytowanie zasobów w edytorze zasobów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vs.resourceview
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio], viewing
- rc files, viewing resources
- Resource View pane
- layouts, previewing resource
- code, viewing resources
- resource editors, viewing resources
- .rc files, viewing resources
- resources [Visual Studio], editing
ms.assetid: ba8bdc07-3f60-43c7-aa5c-d5dd11f0966e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1afa1377b222789243706cf3c5e61f45b4fcd1a1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="viewing-and-editing-resources-in-a-resource-editor"></a>Wyświetlanie i edytowanie zasobów w edytorze zasobów
Każdy typ zasobu ma edytorze zasobów specyficznych dla tego typu zasobu. Można rozmieszczanie, zmienianie rozmiaru, Dodaj formanty i funkcje lub modyfikację aspektów zasobu za pomocą edytora skojarzone. Można również edytować zasobu w [formacie tekstowym](../windows/how-to-open-a-resource-script-file-in-text-format.md) i [format binarny](../windows/opening-a-resource-for-binary-editing.md).  
  
 Niektóre typy zasobów są pojedyncze pliki, które mogą być importowane i używane na różne sposoby; obejmują one mapy bitowe, ikony, kursorów, paski narzędzi i pliki html. Nazwy plików mają takie zasoby jak również [identyfikatory zasobów](../windows/symbols-resource-identifiers.md). Inne osoby, takich jak okien dialogowych, menu i tabele ciągów w projektach systemu Win32 istnieje tylko jako część pliku skryptu (.rc) zasobu lub pliku szablonu (.rct —) zasobu.  
  
> [!NOTE]
>  Właściwości zasobu [można modyfikować przy użyciu okna właściwości](../windows/changing-the-properties-of-a-resource.md).  
  
## <a name="win32-resources"></a>Zasoby Win32  
 Użytkownik ma dostęp do zasobów Win32 [widok zasobów](../windows/resource-view-window.md) okienka.  
  
#### <a name="to-view-a-win32-resource-in-a-resource-editor"></a>Aby wyświetlić zasobów Win32 w edytorze zasobów  
  
1.  Wybierz **widok zasobów** z **widoku** menu.  
  
2.  Jeśli okno Widok zasobów nie jest umieszczony najwyżej okna, kliknij przycisk **widok zasobów** kartę, aby przełączyć go do góry.  
  
3.  Przy pomocy widoku zasobów rozwiń folder dla projektu, który zawiera zasoby, które chcesz wyświetlić. Na przykład jeśli chcesz wyświetlić zasób okna dialogowego, rozwiń folder okna dialogowego.  
  
    > [!NOTE]
    >  Jeśli projekt nie zawiera już plik .rc, zobacz [Tworzenie nowego pliku skryptu zasobu](../windows/how-to-create-a-resource-script-file.md).  
  
4.  Kliknij dwukrotnie zasobu, na przykład IDD_ABOUTBOX.  
  
     Zasób zostanie otwarty w edytorze odpowiednie. Na przykład w przypadku zasoby okna dialogowego zasobu otwierany wewnątrz edytora okien dialogowych.  
  
     Możesz również [wyświetlania zasobów w plik .rc (skrypt zasobu) bez konieczności otwierania projektu](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).  
  
#### <a name="to-delete-an-existing-win-32-resource"></a>Aby usunąć istniejący zasób Win 32  
  
1.  W widokach rozwiń węzeł typu zasobu.  
  
2.  Kliknij prawym przyciskiem myszy na zasobie chcesz usunąć, a następnie wybierz pozycję **usunąć** z menu skrótów.  
  
    > [!NOTE]
    >  Można usunąć zasobu, jeśli istnieje plik .rc jest otwarty w oknie dokumentu poza projektem, przy użyciu tego samego polecenia menu skrótów.  
  
## <a name="resources-in-managed-projects"></a>Zasoby w projektach zarządzanych  
 Ponieważ projektów zarządzanych pliki skryptów zasobów nie jest używana, należy otworzyć zasobów z **Eksploratora rozwiązań**. Można użyć [edytor obrazów](../windows/image-editor-for-icons.md) i [Edytor plików binarnych](binary-editor.md) do pracy z plikami zasobów w projektach zarządzanych. Wszelkie zarządzane zasoby, które chcesz edytować, muszą być powiązanymi zasobami. Edytory zasobów programu Visual Studio nie obsługują edycji zasobów osadzonych.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
#### <a name="to-view-a-managed-resource-in-a-resource-editor"></a>Aby wyświetlić zasobów zarządzanych w edytorze zasobów  
  
1.  W Eksploratorze rozwiązań kliknij dwukrotnie zasobu, na przykład Bitmap1.bmp.  
  
     Zasób zostanie otwarty w edytorze odpowiednie.  
  
#### <a name="to-delete-an-existing-managed-resource"></a>Aby usunąć istniejący zasób zarządzany  
  
1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy zasób chcesz usunąć, a następnie wybierz pozycję **usunąć** z menu skrótów.  
  
### <a name="requirements"></a>Wymagania  
 Brak  
  
## <a name="see-also"></a>Zobacz też  
 [Edytory zasobów](../windows/resource-editors.md)

