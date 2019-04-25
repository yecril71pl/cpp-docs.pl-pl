---
title: Deklarowanie zmiennej opartej na nowej klasie formantów
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.classes.control.variable
helpviewer_keywords:
- variables [MFC], control classes
- control classes [MFC], variables
- classes [MFC], declaring variables based on
ms.assetid: 5722dc38-c0eb-40bd-93da-67a808140d03
ms.openlocfilehash: b3b1a168619c1c111db3e71e1a9562d441cc710d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323011"
---
# <a name="declaring-a-variable-based-on-your-new-control-class"></a>Deklarowanie zmiennej opartej na nowej klasie formantów

Po utworzeniu klasy formantu MFC można zadeklarować zmienną na jego podstawie. Aby zapewnić kontekst nowej zmiennej, należy otworzyć Edytor okien dialogowych i Edytuj okno dialogowe, w której chcesz użyć kontroli nad wielokrotnego użytku. Ponadto okno dialogowe musi już mieć skojarzone z nią klasy. Aby uzyskać informacje na temat używania edytora okien dialogowych, zobacz [Edytor okien dialogowych](../../windows/dialog-editor.md).

### <a name="to-declare-a-variable-based-on-your-reusable-class"></a>Aby zadeklarować zmienną, w oparciu o klasy wielokrotnego użytku

1. Podczas edycji okno dialogowe, przeciągnij formant tego samego typu jako klasa bazowa nowej kontrolki na pasku narzędzi kontrolek na oknie dialogowym.

1. Umieść wskaźnik myszy nad kontrolką porzucone.

1. Naciskaj klawisz CTRL, kliknij dwukrotnie formant.

   [Dodaj zmienną elementu członkowskiego](../../ide/add-member-variable-wizard.md) pojawi się okno dialogowe.

1. W **dostępu** wybierz prawidłowy dostęp dla kontrolki.

1. Kliknij przycisk **zmienna sterująca** pole wyboru.

1. W **nazwa zmiennej** wpisz nazwę.

1. W obszarze **kategorii**, kliknij przycisk **kontroli**.

1. W **identyfikator formantu** listy, wybierz formant, który został dodany. **Typ zmiennej** listy powinien być wyświetlany poprawny typ zmiennej i **kontrolowanie typu** pole powinien być wyświetlany poprawny kontrolek typu.

9. W **komentarz** Dodaj dodatkowe uwagi, które mają być wyświetlane w kodzie.

10. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz także

[Mapowanie komunikatów do funkcji](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Dodawanie funkcji członkowskiej](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Dodawanie zmiennej członkowskiej](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Zastępowanie funkcji wirtualnych](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Handler komunikatów MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Nawigacja w strukturze klas](../../ide/navigating-the-class-structure-visual-cpp.md)
