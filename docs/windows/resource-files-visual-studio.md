---
title: Pliki zasobów (Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio]
- .rc files
- resource files
- resource script files
- resource script files, Win-32 based applications
- resource script files, files updated when editing resources
- resources [Visual Studio], types of resource files
- rct files
- resources [C++]
- rc files
- resource files, types of
- .rct files
- resource script files, unsupported types
ms.assetid: 4d2b6fcc-07cf-4289-be87-83a60f69533c
caps.latest.revision: 18
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 117472c764dd6f13858881275b067600579a0fc8
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/10/2018
---
# <a name="resource-files-visual-studio"></a>Pliki zasobów (Visual Studio)
> [!NOTE]
>  W tym materiale ma zastosowanie do aplikacji klasycznych systemu Windows. Aby uzyskać informacje o zasobach w aplikacjach platformy uniwersalnej systemu Windows, zobacz [Definiowanie zasobów aplikacji](http://msdn.microsoft.com/en-us/476ea844-632c-4467-9ce3-966be1350dd4).  
>   
> Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
>  
> Ponieważ projekty w językach programowania .NET należy używać pliki skryptów zasobów, należy otworzyć zasobów z **Eksploratora rozwiązań**. Można użyć [edytor obrazów](../windows/image-editor-for-icons.md) i [Edytor plików binarnych](binary-editor.md) do pracy z plikami zasobów w projektach zarządzanych. Wszelkie zarządzane zasoby, które chcesz edytować, muszą być powiązanymi zasobami. Edytory zasobów programu Visual Studio nie obsługują edycji zasobów osadzonych.  
  
 Termin "pliku zasobów" może odwoływać się do liczby typów plików, w tym:  
  
-   Plik skryptu (.rc) zasobu programu.  
  
-   Plik zasobów szablonu (.rct —).  
  
-   Istniejące jako plik samodzielny pojedynczego zasobu, takich jak plik mapy bitowej, ikona lub kursora jest określone z pliku .rc.  
  
-   Plik nagłówka wygenerowane przez środowisko deweloperskie, na przykład Resource.h, jest określone w pliku .rc.  
  
 Zasoby można także znaleźć w [innych typów plików](../windows/editable-file-types-for-resources.md) takich jak pliki .exe, dll i .res. Możesz pracować z zasobów i pliki zasobów w projekcie i tych, które nie są częścią bieżącego projektu. Możesz także pracować z plikami zasobów, które nie zostały utworzone w środowisku projektowania programu Visual Studio. Możesz na przykład:  
  
-   Praca z plikami zasobów zagnieżdżone i dołączane warunkowo.  
  
-   Zaktualizuj istniejących zasobów lub przekonwertować je na format Visual C++.  
  
-   Importowanie lub eksportowanie zasobów graficznych do lub z bieżącego pliku zasobu.  
  
-   Obejmują udostępnione lub tylko do odczytu identyfikatorów (symboli), których nie można zmodyfikować przez środowisko deweloperskie.  
  
-   Obejmują zasobów w pliku wykonywalnego (.exe), które nie wymagają edycji (lub nie chcesz edytować) podczas bieżącego projektu, takich jak zasoby, które są wspólne dla kilku projektów.  
  
-   Obejmują typy zasobów, które nie są obsługiwane przez środowisko deweloperskie.  
  
 W tej sekcji omówiono:  
  
-   [Tworzenie nowego pliku skryptu zasobu](../windows/how-to-create-a-resource-script-file.md)  
  
-   [Tworzenie nowego zasobu](../windows/how-to-create-a-resource.md)  
  
-   [Wyświetlanie zasobów w pliku skryptu zasobu](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)  
  
-   [Otwieranie pliku skryptu zasobu w formacie tekstowym](../windows/how-to-open-a-resource-script-file-in-text-format.md)  
  
-   [Czas kompilacji w tym zasobów w](../windows/how-to-include-resources-at-compile-time.md)  
  
-   [Kopiowanie zasobów](../windows/how-to-copy-resources.md)  
  
-   [Za pomocą szablonów zasobów (.rct —)](../windows/how-to-use-resource-templates.md)  
  
-   [Importowanie i eksportowanie zasobów](../windows/how-to-import-and-export-resources.md)  
  
-   [Edytowalne typy plików dla zasobów](../windows/editable-file-types-for-resources.md)  
  
-   [Pliki, których dotyczy edytowanie zasobów](../windows/files-affected-by-resource-editing.md)  
  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Edytory zasobów](../windows/resource-editors.md)   
 [Praca z plikami zasobów](../windows/working-with-resource-files.md)   
 [Menu i innych zasobów](http://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)

