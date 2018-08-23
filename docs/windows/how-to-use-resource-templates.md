---
title: 'Porady: użycie szablonów zasobów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- language-specific template files
- resource templates
- resources [Visual Studio], creating
- rct files
- templates, resource templates
- resources [Visual Studio], templates
- .rct files
ms.assetid: bdfe7060-f98e-4859-8285-9c8570360e9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5bd85dd5c5b6468ca8246fdf11f4068eae928107
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602443"
---
# <a name="how-to-use-resource-templates"></a>Porady: użycie szablonów zasobów

Szablon zasobu jest dostosowane zasobu, który został zapisany jako plik .rct. Szablonu usługi resource następnie może służyć jako punkt wyjścia do tworzenia innych zasobów. Szablony zasobów zaoszczędzić czas w opracowywaniu dodatkowe zasoby lub grupy zasobów, które mają funkcje, takie jak standardowych kontrolek i innych elementów powtórzony. Na przykład możesz chcieć objąć kilka okien dialogowych przycisk Pomoc i ikona logo firmy. Aby zrobić tak szybko, tworzenie nowego szablonu okna dialogowego i dostosować ją przy użyciu logo i przycisk Pomoc.

Po dostosowaniu szablonu zasobów zmiany należy zapisać w folderze szablonu (lub dowolnego miejsca, określona w ścieżce include) tak, że nowy szablon zasobu pojawią się w jego typ zasobu w [Dodaj zasób — okno dialogowe](../windows/add-resource-dialog-box.md). Następnie można użyć nowego szablonu zasobu tak często, zgodnie z potrzebami.

> [!NOTE]
> Podkatalogi katalogu głównego szablonu, można umieścić pliki szablonów specyficzne dla języka. Na przykład, można umieścić pliki szablonów angielskiej w \\< katalog szablonu zasobów\>\1033.

### <a name="to-create-a-template-for-resources"></a>Aby utworzyć szablon dla zasobów

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt.

2. Z menu skrótów wybierz polecenie **Dodaj**, następnie kliknij przycisk **Dodaj nowy element**.

3. W **Dodaj nowy element** dialogowym **szablonów:** okienku wybierz **plik szablonu zasobu (.rct)**.

4. Podaj nazwę i lokalizację nowego pliku .rct, a następnie kliknij przycisk **Otwórz**.

5. Nowy plik .rct zostanie dodany do projektu i pojawia się w **Eksploratora rozwiązań** w obszarze **zasobów** folderu.

   Możesz teraz kliknąć dwukrotnie plik .rct, aby otworzyć go w oknie dokumentu, a następnie dodać zasoby do niego (kliknij prawym przyciskiem myszy plik w oknie dokumentu, a następnie wybierz **Dodaj zasób** z menu skrótów). Następnie można dostosować te zasoby i Zapisz plik .rct.

   > [!NOTE]
   > Podczas tworzenia nowego pliku RCT programu Visual Studio wyszukuje go w 9.0\VC\VCResourceTemplates programu Visual Studio \Program Files\Microsoft, w 9.0\VC\VCResourceTemplates programu Visual Studio \Program Files\Microsoft\\*LCID* () np. 1033 dla języka angielskiego) *lub* dowolnym miejscu [ścieżki dołączania](../windows/how-to-specify-include-directories-for-resources.md). Jeśli chcesz przechowywać pliki śledzenia RCT w innym folderze pliku, na przykład \My dokumenty, musisz tylko dodać ten folder do ścieżki dołączania i programu Visual Studio znajdzie plik RCT.

### <a name="to-convert-an-existing-rc-file-to-an-rct-file"></a>Aby przekonwertować plik .rct istniejący plik .rc

1. [Otwórz plik .rc, jako autonomiczny plik](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

2. Na **pliku** menu, kliknij przycisk **Zapisz \< *swoje filename*> jako**.

3. Określ lokalizację, a następnie kliknij przycisk **OK**.

### <a name="to-create-a-new-resource-from-a-template"></a>Aby utworzyć nowy zasób z szablonu

1. W [widok zasobów](../windows/resource-view-window.md) okienku kliknij prawym przyciskiem myszy plik .rc i wybierz polecenie **Dodaj zasób** z menu skrótów.

2. W **Dodaj zasób** okna dialogowego kliknij znak plus (**+**) obok zasobu, aby rozwinąć węzeł zasobów i wyświetlić wszystkie szablony dostępne dla tego zasobu.

3. Dwukrotnie kliknij szablon, który chcesz użyć.

4. Zmodyfikuj dodano zasobów zgodnie z potrzebami w edytorze zasobów.

   Edytor zasobów automatycznie zapewnia identyfikator unikatowy zasób Możesz poprawić [właściwości zasobu](../windows/changing-the-properties-of-a-resource.md) zgodnie z potrzebami.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Pliki zasobów](../windows/resource-files-visual-studio.md)  
[Edytory zasobów](../windows/resource-editors.md)