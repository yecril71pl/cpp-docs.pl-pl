---
title: "Zmiana właściwości kilku klawiszy skrótów | Dokumentacja firmy Microsoft"
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
- keyboard shortcuts [C++], property changing
- accelerator tables [C++], changing properties
ms.assetid: b55c9bd6-b430-48bb-b942-0e6f21d7abf9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8fbe5ab2202da457c8970d84d304ec97fdedd4a1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="changing-the-properties-of-multiple-accelerator-keys"></a>Zmiana właściwości kilku klawiszy skrótów
### <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>Aby zmienić właściwości kilku klawiszy skrótów  
  
1.  Otwórz tabeli akceleratora klikając odpowiednią ikonę w [widok zasobów](../windows/resource-view-window.md).  
  
    > [!NOTE]
    >  Jeśli projekt nie zawiera już plik .rc, zobacz [Tworzenie nowego pliku skryptu zasobu](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Wybierz klucze akceleratora chcesz zmienić, przytrzymując **CTRL** klucza kliknij każdy z nich.  
  
3.  Przejdź do [okna właściwości](/visualstudio/ide/reference/properties-window) i wpisz wartości, które mają wszystkie wybrane akceleratorów, aby udostępnić.  
  
    > [!NOTE]
    >  Każda wartość modyfikatora pojawia się jako właściwości typu Boolean w oknie właściwości. Jeśli zmienisz [modyfikator](../windows/accelerator-modifier-property.md) wartości w oknie właściwości tabeli akceleratora traktuje new — modyfikator jako dodatek do dowolnego modyfikatory, które były wcześniej dostępne. W związku z tym po ustawieniu wartości modyfikator należy ustawić wszystkie z nich, aby upewnić się, że każdy akceleratora obowiązują te same ustawienia modyfikator.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 **Wymagania**  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Edytowanie tabel akceleratora](../windows/editing-accelerator-tables.md)   
 [Edytor klawiszy skrótów](../windows/accelerator-editor.md)