---
title: Tworzenie ikony lub innego obrazu (edytor obrazów dla ikon) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.bitmap
dev_langs:
- C++
helpviewer_keywords:
- bitmaps [C++]
- images [C++], creating
- resource toolbars
- resources [Visual Studio], creating images
- bitmaps [C++], creating
- graphics [C++], creating
- Image editor [C++], creating images
ms.assetid: 66db3fb2-cfc1-48a2-9bdd-53f61eb7ee30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2138e32b18f2e15de027e3cc04fb1bd7ee46ecd5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874736"
---
# <a name="creating-an-icon-or-other-image-image-editor-for-icons"></a>Tworzenie ikony lub innego obrazu (Edytor obrazów dla ikon)
Możesz utworzyć nowy obraz (mapa bitowa, ikona, kursora lub paska narzędzi), a następnie do dostosowania jego wyglądu Edytor obrazu. Można również utworzyć nowej mapy bitowej deseniem po [szablonu](../windows/how-to-use-resource-templates.md).  
  
### <a name="to-add-a-new-image-resource-to-an-unmanaged-c-project"></a>Aby dodać nowy zasób obrazu do niezarządzanego projektu C++  
  
1.  W [widok zasobów](../windows/resource-view-window.md), kliknij prawym przyciskiem myszy plik .rc, a następnie wybierz **Wstaw zasób** z menu skrótów. (Jeśli masz już istniejący zasób obrazu w pliku .rc, takich jak kursora, użytkownik może po prostu kliknij prawym przyciskiem myszy **kursora** i wybierz polecenie **wstawiania kursora** z menu skrótów.)  
  
    > [!NOTE]
    >  **Uwaga** Jeśli projekt nie zawiera już plik .rc, zobacz [Tworzenie nowego pliku skryptu zasobu](../windows/how-to-create-a-resource-script-file.md).  
  
2.  W [Wstaw zasób — okno dialogowe](../windows/add-resource-dialog-box.md), wybierz typ zasobu obrazu, które chcesz utworzyć (**mapy bitowej**, na przykład) kliknięcie **nowy**.  
  
     Jeśli znak plus (**+**) widoczna obok typ zasobu obrazu w **Wstaw zasób** okno dialogowe, oznacza to, że szablony narzędzi są dostępne. Kliknij znak plus, aby rozwinąć listę szablonów, wybierz szablon, a następnie kliknij przycisk **nowy**.  
  
### <a name="to-add-a-new-image-resource-to-a-project-in-a-net-programming-language"></a>Aby dodać nowy zasób obrazu do projektu w języku programowania .NET  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy folder projektu (na przykład **WindowsApplication1**).  
  
2.  W menu skrótów kliknij **Dodaj**, a następnie wybierz **Dodaj nowy element**.  
  
3.  W **kategorii** okienku rozwiń **elementy lokalne projektu** folder, a następnie wybierz **zasobów**.  
  
4.  W **szablony** okienku, wybierz typ zasobu, które chcesz dodać do projektu.  
  
     Zasób zostanie dodany do projektu w Eksploratorze rozwiązań i zasób zostanie otwarty w [edytor obrazów](../windows/image-editor-for-icons.md). Po wykonaniu użyć narzędzi dostępnych w edytorze obrazów do modyfikowania obrazu. Aby uzyskać więcej informacji o dodawaniu obrazów do zarządzanego projektu, zobacz [podczas ładowania obrazu w czasie projektowania](/dotnet/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms).  
  
    > [!NOTE]
    >  Wszelkie zarządzane zasoby, które chcesz edytować, muszą być powiązanymi zasobami. Edytory zasobów programu Visual Studio nie obsługują edycji zasobów osadzonych. Aby uzyskać więcej informacji, zobacz [tworzenie plików zasobów](/dotnet/framework/resources/creating-resource-files-for-desktop-apps) w *.NET Framework — Przewodnik programisty*.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Wymagania  
  
 Brak  
  
## <a name="see-also"></a>Zobacz też  
 [Ikony i kursory: zasoby obrazów do wyświetlania na urządzeniach](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)   
 [Konwertowanie map bitowych na paski narzędzi](../windows/converting-bitmaps-to-toolbars.md)   
 [Tworzenie nowych pasków narzędzi](../windows/creating-new-toolbars.md)   
 [Edytowanie zasobów graficznych](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)

