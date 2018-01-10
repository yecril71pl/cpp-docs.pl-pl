---
title: Edytor okien dialogowych | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.editors.dialog.dialog
- vc.editors.dialog.F1
dev_langs: C++
helpviewer_keywords:
- resource editors, Dialog editor
- editors, dialog boxes
- Dialog editor
- dialog boxes, editing
ms.assetid: d94884ef-2cca-49d8-9b58-775f34848134
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a18ed3aad1d3a9ea697ac815658b5eba8d99bff1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="dialog-editor"></a>Edytor okien dialogowych
Edytor okien dialogowych pozwala na tworzenie lub edytowanie zasobów okien dialogowych. Otwórz Edytor okien dialogowych klikając dwukrotnie plik .rc okno dialogowe okno Widok zasobów (**widoku &#124; Widok zasobów**). Należy zauważyć, że widok zasobów nie jest dostępny w wersji Express.  
  
 Jednym z pierwszych kroków w tworzeniu nowego okna dialogowego (lub szablonu okna dialogowego) jest dodanie formantów do okna dialogowego. W edytorze okien dialogowych można rozmieścić formanty w celu dopasowania do określonego rozmiaru, kształtu lub wyrównania lub przenosić je w celu pracy z oknem dialogowym. W łatwy sposób można również usunąć formant.  
  
 Okno dialogowe można przechowywać jako szablon w celu ponownego użycia. Można także łatwo przełączyć się między projektowaniem okna dialogowego a edycją kodu, który go implementuje.  
  
 Jest również możliwe edytowanie właściwości jednego lub wielu formantów w edytorze okien dialogowych. Można zmienić kolejność tabulacji, czyli kolejność, w której formanty uzyskują fokus podczas naciskania klawisza TAB, lub można zdefiniować klawisz dostępu (kombinację klawiszy), która pozwala użytkownikowi na wybór formantu przy użyciu klawiatury. Aby uzyskać listę kluczy dostępu do istniejących, zobacz [klucze akceleratora dla edytora okien dialogowych](../windows/accelerator-keys-for-the-dialog-editor.md).  
  
 Edytor okien dialogowych pozwala na używanie niestandardowych formantów, w tym formantów ActiveX. Ponadto można edytować [widok formularza](../mfc/reference/cformview-class.md), [widoków rekordów](../data/record-views-mfc-data-access.md), lub [paski dialogowe](../mfc/dialog-bars.md).  
  
 Począwszy od programu Visual Studio 2015, można użyć edytora okien dialogowych do definiowania układów dynamiczne, które określają sposób formanty przenoszenie i zmienianie rozmiaru, gdy użytkownik zmienia rozmiar okna dialogowego. Aby uzyskać więcej informacji, zobacz [układ dynamiczny](../mfc/dynamic-layout.md).  
  
-   [Tworzenie nowego okna dialogowego](../windows/creating-a-new-dialog-box.md)  
  
-   [Tworzenie okna dialogowego użytkowników nie może zamknąć w czasie wykonywania](../windows/creating-a-dialog-box-that-users-cannot-exit.md)  
  
-   [Pokazywanie i ukrywanie paska narzędzi Edytora okien dialogowych](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)  
  
-   [Przełączanie między Edytor okien dialogowych i kodem](../windows/switching-between-dialog-box-controls-and-code.md)  
  
-   [Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)  
  
-   [Dodawanie obsługi zdarzeń dla kontrolek okna dialogowego](../windows/adding-event-handlers-for-dialog-box-controls.md)  
  
-   [Testowanie okna dialogowego](../windows/testing-a-dialog-box.md)  
  
-   [Klucze akceleratora dla Edytora okien dialogowych](../windows/accelerator-keys-for-the-dialog-editor.md)  
  
-   [Rozwiązywanie problemów z Edytorem okien dialogowych](../windows/troubleshooting-the-dialog-editor.md)  
  
    > [!TIP]
    >  Podczas używania edytora okien dialogowych, w wielu przypadkach, kliknięcie prawym przyciskiem myszy wyświetli menu skrótów z najczęściej używanymi poleceniami.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Edytory zasobów](../windows/resource-editors.md)   
 [Formanty](../mfc/controls-mfc.md)   
 [Klasy formantów](../mfc/control-classes.md)   
 [Klasy okien dialogowych](../mfc/dialog-box-classes.md)   
 [Kontrolki okna dialogowego i typy zmiennych](../ide/dialog-box-controls-and-variable-types.md)

