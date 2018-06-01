---
title: Dodawanie zmiennej członkowskiej (Visual C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.classes.member.variable
dev_langs:
- C++
helpviewer_keywords:
- member variables, adding
- member variables
ms.assetid: 437783bd-8eb4-4508-8b73-7380116e9d71
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa2a8ef8f7bcdc2d90893acdad98705c9588a5d5
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "33325734"
---
# <a name="adding-a-member-variable--visual-c"></a>Dodawanie zmiennej członkowskiej (Visual C++)
Można dodać zmienną członkowską do klasy przy użyciu widoku klasy. Zmienne Członkowskie mogą być dla [danych wymiana i Walidacja danych](../mfc/dialog-data-exchange-and-validation.md), lub mogą być ogólne. Kreator zmiennej elementu członkowskiego danych jest specjalnie zaprojektowane do podjąć odpowiednie informacje i użyj go, aby wstawić elementów w plikach źródłowych w odpowiednich lokalizacjach. Można dodać zmienną członkowską z [Edytor okien dialogowych](../windows/dialog-editor.md) w [widok zasobów](../windows/resource-view-window.md), lub z [widoku klasy](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925).  
  
> [!NOTE]
>  Podczas projektowania i wdrażania okno dialogowe, może okazać bardziej efektywne przy użyciu okna dialogowego edytora w celu Dodaj formanty okna dialogowego, a następnie wdrożyć zmienne Członkowskie formantów.  
  
### <a name="to-add-a-member-variable-for-a-dialog-control-in-resource-view-using-the-add-member-variable-wizard"></a>Aby dodać zmienną członkowską dla formantu okna dialogowego w widoku zasobów za pomocą Kreatora dodawania zmiennej elementu członkowskiego  
  
1.  W widokach rozwiń węzeł projektu i węzeł okna dialogowego, aby wyświetlić listę okien dialogowych projektu.  
  
2.  Kliknij dwukrotnie okno dialogowe, do której chcesz dodać zmiennej członka, aby otworzyć go w edytorze okien dialogowych.  
  
3.  W oknie dialogowym wyświetlany w edytorze okien dialogowych kliknij prawym przyciskiem myszy formantu, do której chcesz dodać zmiennej członka.  
  
4.  W menu skrótów kliknij **Dodaj zmienną** do wyświetlenia [Dodaj kreatora zmiennej elementu członkowskiego](../ide/add-member-variable-wizard.md).  
  
    > [!NOTE]
    >  Wartość domyślna znajduje się już w **Identyfikatora formantu**.  
  
5.  Podaj informacje w polach odpowiedniego kreatora. Zobacz [formantów okna dialogowego i typy zmiennych](../ide/dialog-box-controls-and-variable-types.md) Aby uzyskać więcej informacji.  
  
6.  Kliknij przycisk **Zakończ** można dodać definicji i wdrażanie kodu do projektu i zamknąć kreatora.  
  
### <a name="to-add-a-member-variable-from-class-view-using-the-add-member-variable-wizard"></a>Aby dodać zmienną członkowską z widoku klasy przy użyciu Kreatora dodawania zmiennej elementu członkowskiego  
  
1.  W [widoku klasy](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), rozwiń węzeł projektu, aby wyświetlić klasy w projekcie.  
  
2.  Kliknij prawym przyciskiem myszy klasę, do której chcesz dodać zmienną.  
  
3.  W menu skrótów kliknij **Dodaj**, a następnie kliknij przycisk **Dodaj zmienną** do wyświetlania elementu członkowskiego zmiennej Kreatora dodawania.  
  
4.  Podaj informacje w polach odpowiedniego kreatora. Zobacz [Dodaj kreatora zmiennej elementu członkowskiego](../ide/add-member-variable-wizard.md) szczegółowe informacje.  
  
5.  Kliknij przycisk **Zakończ** można dodać definicji i wdrażanie kodu do projektu i zamknąć kreatora.  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie funkcji z kreatorami kodów](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Dodawanie klasy](../ide/adding-a-class-visual-cpp.md)   
 [Dodawanie funkcji członkowskiej](../ide/adding-a-member-function-visual-cpp.md)   
 [Handler komunikatów MFC](../mfc/reference/adding-an-mfc-message-handler.md)   
 [Nawigacja w strukturze klas](../ide/navigating-the-class-structure-visual-cpp.md)