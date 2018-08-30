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
ms.openlocfilehash: d20611d2cc5e4b391e2dafdef614dd5173d32ef7
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43207301"
---
# <a name="adding-a-member-variable--visual-c"></a>Dodawanie zmiennej członkowskiej (Visual C++)
Możesz dodać zmienną członkowską do klasy za pomocą widoku klas. Zmienne składowe mogą być albo dla [wymiany danych i sprawdzanie poprawności danych](../mfc/dialog-data-exchange-and-validation.md), lub może być ogólny. Kreator zmiennej składowej danych jest specjalnie przeznaczona do podjąć odpowiednie informacje i używać go do wstawienia elementów w plikach źródłowych w odpowiednich lokalizacjach. Można dodać zmienną członkowską z [Edytor okien dialogowych](../windows/dialog-editor.md) w [widok zasobów](../windows/resource-view-window.md), lub z [Widok klas](https://msdn.microsoft.com/8d7430a9-3e33-454c-a9e1-a85e3d2db925).  
  
> [!NOTE]
>  Podczas projektowania i implementowania okno dialogowe, może okazać się bardziej wydajne, można użyć okna dialogowego edytora, aby dodać formanty okna dialogowego, a następnie wdrożyć zmiennych składowych kontrolek.  
  
### <a name="to-add-a-member-variable-for-a-dialog-control-in-resource-view-using-the-add-member-variable-wizard"></a>Aby dodać zmienną składową dla formantu w oknie dialogowym w widoku zasobów za pomocą Kreatora dodawania zmiennej składowej  
  
1.  W widoku zasobu rozwiń węzeł projektu i węzeł okna dialogowego, aby wyświetlić listę okien dialogowych projektu.  
  
2.  Dwukrotnie kliknij okno dialogowe, do którego chcesz dodać zmienną członkowską, aby otworzyć go w edytorze okien dialogowych.  
  
3.  W oknie dialogowym wyświetlany w edytorze okien dialogowych kliknij prawym przyciskiem myszy formant, do którego chcesz dodać zmienną członkowską.  
  
4.  W menu skrótów kliknij **Dodaj zmienną** do wyświetlenia [Dodaj kreatora zmiennej elementu członkowskiego](../ide/add-member-variable-wizard.md).  
  
    > [!NOTE]
    >  Wartość domyślna znajduje się już w **identyfikator formantu**.  
  
5.  Podaj informacje w polach odpowiedniego kreatora. Zobacz [formantów okna dialogowego i typy zmiennych](../ide/dialog-box-controls-and-variable-types.md) Aby uzyskać więcej informacji.  
  
6.  Kliknij przycisk **Zakończ** Dodaj definicję i implementację kodu do projektu i zamknąć kreatora.  
  
### <a name="to-add-a-member-variable-from-class-view-using-the-add-member-variable-wizard"></a>Aby dodać zmienną członkowską z widoku klasy za pomocą Kreatora dodawania zmiennej składowej  
  
1.  W [Widok klas](https://msdn.microsoft.com/8d7430a9-3e33-454c-a9e1-a85e3d2db925), rozwiń węzeł projektu, aby wyświetlić klasy w projekcie.  
  
2.  Kliknij prawym przyciskiem myszy klasę, do której chcesz dodać zmienną.  
  
3.  W menu skrótów kliknij **Dodaj**, a następnie kliknij przycisk **Dodaj zmienną** wyświetlić Dodaj kreatora zmiennej elementu członkowskiego.  
  
4.  Podaj informacje w polach odpowiedniego kreatora. Zobacz [Dodaj kreatora zmiennej elementu członkowskiego](../ide/add-member-variable-wizard.md) Aby uzyskać szczegółowe informacje.  
  
5.  Kliknij przycisk **Zakończ** Dodaj definicję i implementację kodu do projektu i zamknąć kreatora.  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie funkcji za pomocą kreatorów kodu](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Dodawanie klasy](../ide/adding-a-class-visual-cpp.md)   
 [Dodawanie funkcji członkowskiej](../ide/adding-a-member-function-visual-cpp.md)   
 [Handler komunikatów MFC](../mfc/reference/adding-an-mfc-message-handler.md)   
 [Nawigacja w strukturze klas](../ide/navigating-the-class-structure-visual-cpp.md)