---
title: "Otwieranie zasobów do edycji plików binarnych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.binary
dev_langs: C++
helpviewer_keywords:
- binary data, editing
- resources [Visual Studio], opening for binary editing
ms.assetid: d3cdb0e4-da66-410d-8e49-b29073ff2929
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c05aa708691ae88a9fe9f345825b54d445683110
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="opening-a-resource-for-binary-editing"></a>Otwieranie zasobów do edycji plików binarnych
### <a name="to-open-a-windows-desktop-resource-for-binary-editing"></a>Aby otworzyć do edycji plików binarnych zasobu pulpitu systemu Windows  
  
1.  W [widok zasobów](../windows/resource-view-window.md), wybierz plik określonego zasobu, który chcesz edytować.  
  
    > [!NOTE]
    >  Jeśli projekt nie zawiera już plik .rc, zobacz [Tworzenie nowego pliku skryptu zasobu](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Kliknij prawym przyciskiem myszy zasób, a następnie kliknij przycisk **Otwórz danych binarnych** z menu skrótów.  
  
    > [!NOTE]
    >  Jeśli używasz [widok zasobów](../windows/resource-view-window.md) okno, aby otworzyć zasobu w formacie, że program Visual Studio nie rozpoznaje (na przykład RCDATA lub zasobów niestandardowych), zasobu automatycznie jest otwarty w edytorze binarnym.  
  
### <a name="to-open-a-managed-resource-for-binary-editing"></a>Aby otworzyć do edycji plików binarnych zasobu zarządzanego  
  
1.  W Eksploratorze rozwiązań wybierz plik określonego zasobu, który chcesz edytować.  
  
2.  Kliknij prawym przyciskiem myszy zasób, a następnie wybierz pozycję **Otwórz za pomocą** z menu skrótów.  
  
3.  W **Otwórz za pomocą** oknie dialogowym wybierz **edytora plików binarnych**.  
  
    > [!NOTE]
    >  Można użyć [edytor obrazów](../windows/image-editor-for-icons.md) i [Edytor plików binarnych](binary-editor.md) do pracy z plikami zasobów w projektach zarządzanych. Wszelkie zarządzane zasoby, które chcesz edytować, muszą być powiązanymi zasobami. Edytory zasobów programu Visual Studio nie obsługują edycji zasobów osadzonych.  
  
    > [!NOTE]
    >  Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](https://msdn.microsoft.com/library/f45fce5x.aspx) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](https://msdn.microsoft.com/library/xbx3z216.aspx). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).   
  
 ![Edytor plików binarnych](../mfc/media/vcbinaryeditor2.gif "vcBinaryEditor2")  
Dane binarne dla okna dialogowego wyświetlane w edytorze danych binarnych  
  
 Tylko niektóre wartości ASCII są reprezentowane w edytorze binarnym (0x20 za pośrednictwem 0x7E). Znaki rozszerzone są wyświetlane jako okresy w sekcji wartość ASCII w edytorze binarnym (prawym panelu). Znaki "drukowalne" są wartości ASCII 32 do 126.  
  
> [!NOTE]
>  Jeśli chcesz użyć Edytor plików binarnych w zasobie już edytowany w innym oknie edytora, należy najpierw zamknąć pozostałe okna edytora.  
  
 **Wymagania**  
  
 Brak  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor plików binarnych](binary-editor.md)

