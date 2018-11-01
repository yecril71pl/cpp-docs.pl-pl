---
title: Dodawanie zmiennej członkowskiej (Visual C++)
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.classes.member.variable
helpviewer_keywords:
- member variables, adding
- member variables
ms.assetid: 437783bd-8eb4-4508-8b73-7380116e9d71
ms.openlocfilehash: 3c7f64fae00e489da7c71bcfe5731db72e1afdf7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595782"
---
# <a name="adding-a-member-variable--visual-c"></a>Dodawanie zmiennej członkowskiej (Visual C++)

Możesz dodać zmienną członkowską do klasy za pomocą widoku klas. Zmienne składowe mogą być albo dla [wymiany danych i sprawdzanie poprawności danych](../mfc/dialog-data-exchange-and-validation.md), lub może być ogólny. Kreator zmiennej składowej danych jest specjalnie przeznaczona do podjąć odpowiednie informacje i używać go do wstawienia elementów w plikach źródłowych w odpowiednich lokalizacjach. Można dodać zmienną członkowską z [Edytor okien dialogowych](../windows/dialog-editor.md) w [widok zasobów](../windows/resource-view-window.md), lub z [Widok klas](/visualstudio/ide/viewing-the-structure-of-code).

> [!NOTE]
>  Podczas projektowania i implementowania okno dialogowe, może okazać się bardziej wydajne, można użyć okna dialogowego edytora, aby dodać formanty okna dialogowego, a następnie wdrożyć zmiennych składowych kontrolek.

### <a name="to-add-a-member-variable-for-a-dialog-control-in-resource-view-using-the-add-member-variable-wizard"></a>Aby dodać zmienną składową dla formantu w oknie dialogowym w widoku zasobów za pomocą Kreatora dodawania zmiennej składowej

1. W widoku zasobu rozwiń węzeł projektu i węzeł okna dialogowego, aby wyświetlić listę okien dialogowych projektu.

1. Dwukrotnie kliknij okno dialogowe, do którego chcesz dodać zmienną członkowską, aby otworzyć go w edytorze okien dialogowych.

1. W oknie dialogowym wyświetlany w edytorze okien dialogowych kliknij prawym przyciskiem myszy formant, do którego chcesz dodać zmienną członkowską.

1. W menu skrótów kliknij **Dodaj zmienną** do wyświetlenia [Dodaj kreatora zmiennej elementu członkowskiego](../ide/add-member-variable-wizard.md).

   > [!NOTE]
   > Wartość domyślna znajduje się już w **identyfikator formantu**.

1. Podaj informacje w polach odpowiedniego kreatora. Zobacz [formantów okna dialogowego i typy zmiennych](../ide/dialog-box-controls-and-variable-types.md) Aby uzyskać więcej informacji.

1. Kliknij przycisk **Zakończ** Dodaj definicję i implementację kodu do projektu i zamknąć kreatora.

### <a name="to-add-a-member-variable-from-class-view-using-the-add-member-variable-wizard"></a>Aby dodać zmienną członkowską z widoku klasy za pomocą Kreatora dodawania zmiennej składowej

1. W [Widok klas](/visualstudio/ide/viewing-the-structure-of-code), rozwiń węzeł projektu, aby wyświetlić klasy w projekcie.

1. Kliknij prawym przyciskiem myszy klasę, do której chcesz dodać zmienną.

1. W menu skrótów kliknij **Dodaj**, a następnie kliknij przycisk **Dodaj zmienną** wyświetlić Dodaj kreatora zmiennej elementu członkowskiego.

1. Podaj informacje w polach odpowiedniego kreatora. Zobacz [Dodaj kreatora zmiennej elementu członkowskiego](../ide/add-member-variable-wizard.md) Aby uzyskać szczegółowe informacje.

1. Kliknij przycisk **Zakończ** Dodaj definicję i implementację kodu do projektu i zamknąć kreatora.

## <a name="see-also"></a>Zobacz też

[Dodawanie funkcji za pomocą kreatorów kodu](../ide/adding-functionality-with-code-wizards-cpp.md)<br>
[Dodawanie klasy](../ide/adding-a-class-visual-cpp.md)<br>
[Dodawanie funkcji członkowskiej](../ide/adding-a-member-function-visual-cpp.md)<br>
[Handler komunikatów MFC](../mfc/reference/adding-an-mfc-message-handler.md)<br>
[Nawigacja w strukturze klas](../ide/navigating-the-class-structure-visual-cpp.md)