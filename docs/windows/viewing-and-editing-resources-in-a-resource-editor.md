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
ms.openlocfilehash: 5fca755c46d3fc5628adc2c724b9307a346d1fe7
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014006"
---
# <a name="viewing-and-editing-resources-in-a-resource-editor"></a>Wyświetlanie i edytowanie zasobów w edytorze zasobów
Każdy typ zasobu ma **zasobów** edytora specyficznych dla typu zasobu. Można zmienić kolejność, zmiany rozmiaru, dodawać formanty i funkcje lub inny sposób modyfikować aspektów zasobu za pomocą edytora skojarzone. Można również edytować zasobu w [format tekstu](../windows/how-to-open-a-resource-script-file-in-text-format.md) i [format binarny](../windows/opening-a-resource-for-binary-editing.md).  
  
 Niektóre typy zasobów są pojedyncze pliki, które mogą być importowane i używane na różne sposoby; obejmują one map bitowych, ikon, kursorów, paski narzędzi i pliki html. Takie zasoby mają nazwy plików także [identyfikatory zasobów](../windows/symbols-resource-identifiers.md). Inne, takie jak okna dialogowe, menu i tabele ciągów w projektach systemu Win32, istnieje tylko jako część pliku skryptu (.rc) zasobów lub zasobu, plik szablonu (.rct).  
  
> [!NOTE]
>  Właściwości zasobu [można zmodyfikować w oknie właściwości](../windows/changing-the-properties-of-a-resource.md).  
  
## <a name="win32-resources"></a>Zasoby Win32  
 Dostęp zasobów Win32 w [widok zasobów](../windows/resource-view-window.md) okienka.  
  
### <a name="to-view-a-win32-resource-in-a-resource-editor"></a>Aby wyświetlić zasób Win32 w edytorze zasobów  
  
1.  Wybierz **widok zasobów** z **widoku** menu.  
  
2.  Jeśli **widok zasobów** okno nie jest umieszczony najwyżej okna, kliknij przycisk **widok zasobów** kartę, aby przełączyć go do góry.  
  
3.  Z **widok zasobów**, rozwiń folder dla projektu, który zawiera zasoby, które chcesz wyświetlić. Na przykład, jeśli chcesz wyświetlić zasobu okna dialogowego, rozwiń **okna dialogowego** folderu.  
  
    > [!NOTE]
    >  Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).  
  
4.  Kliknij dwukrotnie zasób, na przykład **IDD_ABOUTBOX**.  
  
     Zasób zostanie otwarty w edytorze odpowiednie. Na przykład dla zasobów okna dialogowego, zasobu otwiera wewnątrz **okna dialogowego** edytora.  
  
     Możesz również [wyświetlania zasobów w pliku .rc (skrypt zasobu) bez konieczności otwierania projektu](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).  
  
### <a name="to-delete-an-existing-win-32-resource"></a>Aby usunąć istniejący zasób Win 32  
  
1.  W **widok zasobów**, rozwiń węzeł dla typu zasobu.  
  
2.  Kliknij prawym przyciskiem myszy do zasobu, które chcesz usunąć, a następnie wybierz **Usuń** z menu skrótów.  
  
    > [!NOTE]
    >  Możesz usunąć zasób za pomocą tego samego polecenia w menu skrótów, gdy plik .rc jest otwarty w oknie dokumentu poza projektem.  
  
## <a name="resources-in-managed-projects"></a>Zasoby w projektach zarządzanych  
 Ponieważ projektów zarządzanych plików skryptu zasobu nie jest używany, należy otworzyć swoich zasobów przed **Eksploratora rozwiązań**. Możesz użyć [edytora obrazów](../windows/image-editor-for-icons.md) i [edytorze binarnym](binary-editor.md) do pracy z plikami zasobów w projektach zarządzanych. Wszelkie zarządzane zasoby, które chcesz edytować, muszą być powiązanymi zasobami. Edytory zasobów programu Visual Studio nie obsługują edycji zasobów osadzonych.  
  
 Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).  
  
### <a name="to-view-a-managed-resource-in-a-resource-editor"></a>Aby wyświetlić zasobów zarządzanych w edytorze zasobów  
  
1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie zasób, na przykład **Bitmap1.bmp**.  
  
     Zasób zostanie otwarty w edytorze odpowiednie.  
  
### <a name="to-delete-an-existing-managed-resource"></a>Aby usunąć istniejący zasób zarządzany  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy zasób, o których chcesz usunąć, a następnie wybierz **Usuń** z menu skrótów.  
  
## <a name="requirements"></a>Wymagania  
 Brak  
  
## <a name="see-also"></a>Zobacz też  
 [Edytory zasobów](../windows/resource-editors.md)