---
title: Okna dialogowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- modeless dialog boxes [MFC], MFC dialog boxes
- MFC, dialog boxes
- modal dialog boxes [MFC], MFC dialog boxes
- CDialog class [MFC], MFC dialog boxes
- MFC dialog boxes
ms.assetid: e4feea1a-8360-4ccb-9b84-507f1ccd9ef3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c8de283d81aa9d260b891f285f06555dc67895f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346678"
---
# <a name="dialog-boxes"></a>Okna dialogowe
Dla systemu Windows często komunikują się z aplikacjami użytkownika za pomocą okien dialogowych. Klasa [cdialog —](../mfc/reference/cdialog-class.md) udostępnia interfejs dla zarządzania okien dialogowych, Edytor okien dialogowych programu Visual C++ ułatwia projektowanie okien dialogowych i utworzyć ich zasobów szablonu okna dialogowego i kreatorów kodu uprościć proces inicjowania i Sprawdzanie poprawności formantów w oknie dialogowym i zbierania wartości wprowadzonej przez użytkownika.  
  
 Okna dialogowe zawierać formantów, w tym:  
  
-   Formanty standardowe systemu Windows takich jak edytować pola, przyciski pola listy, pola kombi, drzewa formantów, kontrolki listy i wskaźniki postępu.  
  
-   Kontrolki ActiveX.  
  
-   Formanty rysowane przez właściciela: formanty, które są odpowiedzialne za narysowanie w oknie dialogowym.  
  
 Większość okien dialogowych są modalne, które wymagają użytkownika zamknąć okno dialogowe przed rozpoczęciem korzystania z innych części programu. Ale istnieje możliwość utworzenia Niemodalne okna dialogowe, które umożliwiają użytkownikom pracę z innych okien przy otwartym oknie dialogowym. MFC obsługuje oba rodzaje okno dialogowe z klasą `CDialog`. Formanty ułożone i zarządzane przy użyciu zasobu szablonu okna dialogowego, utworzone za pomocą [Edytor okien dialogowych](../windows/dialog-editor.md).  
  
 [Arkusze właściwości](../mfc/property-sheets-mfc.md), nazywane również karcie okna dialogowe, są zawierające "stron" distinct okno dialogowe formantów okna dialogowe. Każda strona ma folder "Karta" u góry pliku. Na karcie kliknięcie powoduje wyświetlenie strony na początku okna dialogowego.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Przykład: wyświetlanie okna dialogowego za pomocą polecenia menu](../mfc/example-displaying-a-dialog-box-via-a-menu-command.md)  
  
-   [Składniki okna dialogowego w strukturze](../mfc/dialog-box-components-in-the-framework.md)  
  
-   [Modalne i Niemodalne okna dialogowe](../mfc/modal-and-modeless-dialog-boxes.md)  
  
-   [Arkusze właściwości i strony właściwości](../mfc/property-sheets-and-property-pages-mfc.md) w oknie dialogowym  
  
-   [Tworzenie zasobu okna dialogowego](../mfc/creating-the-dialog-resource.md)  
  
-   [Tworzenie klasy okien dialogowych za pomocą kreatorów kodu](../mfc/creating-a-dialog-class-with-code-wizards.md)  
  
-   [Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)  
  
-   [Wymiana danych okna dialogowego (DDX) i sprawdzania poprawności (DDV)](../mfc/dialog-data-exchange-and-validation.md)  
  
-   [Bezpieczny dostęp do formantów w oknie dialogowym](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)  
  
-   [Mapowanie komunikatów systemu Windows na klasę](../mfc/mapping-windows-messages-to-your-class.md)  
  
-   [Powszechnie zastępowane funkcje składowe](../mfc/commonly-overridden-member-functions.md)  
  
-   [Powszechnie dodawane funkcje składowe](../mfc/commonly-added-member-functions.md)  
  
-   [Klasy wspólnych okien dialogowych](../mfc/common-dialog-classes.md)  
  
-   [Okna dialogowe w OLE](../mfc/dialog-boxes-in-ole.md)  
  
-   Tworzenie aplikacji interfejsu użytkownika, którego to okno dialogowe: zobacz [CMNCTRL1](../visual-cpp-samples.md) lub [CMNCTRL2](../visual-cpp-samples.md) przykładowe programy. Kreator aplikacji udostępnia również tej opcji.  
  
-   [Przykłady](../mfc/dialog-sample-list.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)
