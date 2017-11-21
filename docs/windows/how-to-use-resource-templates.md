---
title: "Porady: użycie szablonów zasobów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- language-specific template files
- resource templates
- resources [Visual Studio], creating
- rct files
- templates, resource templates
- resources [Visual Studio], templates
- .rct files
ms.assetid: bdfe7060-f98e-4859-8285-9c8570360e9d
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a072fb02c1821e2174671465d570944078b08f7a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-use-resource-templates"></a>Porady: użycie szablonów zasobów
Szablon zasobu jest zapisany jako plik .rct — zasób dostosowany. Szablon zasobu może następnie służyć jako punkt początkowy do tworzenia innych zasobów. Szablony zasobów zaoszczędzić czas podczas opracowywania dodatkowych zasobów lub grup zasobów, które mają funkcje, takie jak standardowych kontrolek i inne elementy powtórzony. Na przykład można objąć kilka okien dialogowych przycisk Pomoc i ikony logo firmy. Aby wykonać tak szybko, Utwórz nowy szablon — okno dialogowe i dostosować go za pomocą logo i przycisk Pomoc.  
  
 Dostosowaną szablonu zasobów zmiany należy zapisać w folderze szablonów (lub dowolnej lokalizacji określona w ścieżce dołączanych) tak, aby nowy szablon zasobów zostanie wyświetlony w obszarze jej typ zasobu w [okno dialogowe dodawania zasobów](../windows/add-resource-dialog-box.md). Można następnie użyć nowego szablonu zasobów tak często, zgodnie z potrzebami.  
  
> [!NOTE]
>  Pliki szablonów specyficzne dla języka można umieścić w podkatalogach katalogu głównego szablonu. Na przykład można umieścić pliki szablonów angielskiej w \\< katalog szablonu zasobów\>\1033.  
  
### <a name="to-create-a-template-for-resources"></a>Aby utworzyć szablon dla zasobów  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt.  
  
2.  Z menu skrótów wybierz **Dodaj**, następnie kliknij przycisk **Dodaj nowy element**.  
  
3.  W **Dodaj nowy element** okna dialogowego, **szablony:** okienku wybierz **pliku szablonu zasobów (.rct —)**.  
  
4.  Podaj nazwę i lokalizację dla nowego pliku .rct — i kliknij przycisk **Otwórz**.  
  
5.  Nowy plik .rct — zostanie dodany do projektu i zostanie wyświetlony w Eksploratorze rozwiązań w obszarze **zasobów** folderu.  
  
     Możesz teraz kliknij dwukrotnie plik .rct —, aby otworzyć go w oknie dokumentu, a następnie dodać zasoby do niego (kliknij prawym przyciskiem myszy plik w oknie dokumentu i wybierz polecenie **dodawania zasobów** z menu skrótów). Można dostosować tych zasobów i Zapisz plik .rct —.  
  
    > [!NOTE]
    >  Podczas tworzenia nowego pliku rct — Visual Studio wyszukuje go w \Program Files\Microsoft 9.0\VC\VCResourceTemplates programu Visual Studio, w 9.0\VC\VCResourceTemplates programu Visual Studio \Program Files\Microsoft\\*LCID* () np. 1033 dla języka angielskiego) *lub* dowolne miejsce [zawierają ścieżki](../windows/how-to-specify-include-directories-for-resources.md). Jeśli mają być przechowywane pliki rct — w innym folderze pliku, na przykład \My dokumenty, wystarczy dodać ten folder do ścieżki dołączania i Visual Studio znajdzie plik rct —.  
  
### <a name="to-convert-an-existing-rc-file-to-an-rct-file"></a>Aby przekonwertować istniejący plik .rc .rct — plik  
  
1.  [Otwórz plik .rc jako autonomiczny plik](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).  
  
2.  Na **pliku** menu, kliknij przycisk  **zapisać \<* Twojego filename*> jako **.  
  
3.  Określ lokalizację, a następnie kliknij przycisk **OK**.  
  
### <a name="to-create-a-new-resource-from-a-template"></a>Aby utworzyć nowy zasób z szablonu  
  
1.  W [widok zasobów](../windows/resource-view-window.md) okienku kliknij prawym przyciskiem myszy plik .rc i wybierz polecenie **dodawania zasobów** z menu skrótów.  
  
2.  W **dodawania zasobów** oknie dialogowym kliknij znak plus (**+**) obok zasobu rozwiń węzeł zasobów i zobaczyć wszystkie szablony dostępne dla tego zasobu.  
  
3.  Dwukrotnie kliknij szablon, który ma być używany.  
  
4.  Zmodyfikuj dodano zasobów zgodnie z potrzebami w edytorze zasobów.  
  
     Edytor zasobów automatycznie zawiera identyfikator unikatowy zasób. Można skorygować [właściwości zasobów](../windows/changing-the-properties-of-a-resource.md) zgodnie z potrzebami.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.*  
  
 Wymagania  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki zasobów](../windows/resource-files-visual-studio.md)   
 [Edytory zasobów](../windows/resource-editors.md)