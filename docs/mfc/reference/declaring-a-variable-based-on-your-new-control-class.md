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
ms.openlocfilehash: 994f81524001a80d1cf0dd3783b9de742d61e84d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365845"
---
# <a name="declaring-a-variable-based-on-your-new-control-class"></a>Deklarowanie zmiennej opartej na nowej klasie formantów

Po utworzeniu klasy kontroli MFC, można zadeklarować zmienną na jej podstawie. Aby zapewnić kontekst dla nowej zmiennej, należy otworzyć edytor okien dialogowych i edytować okno dialogowe, w którym ma być używane kontrolki wielokrotnego użytku. Ponadto okno dialogowe musi mieć już skojarzoną z nim klasę. Aby uzyskać informacje na temat korzystania z edytora okien dialogowych, zobacz [Edytor okien dialogowych](../../windows/dialog-editor.md).

### <a name="to-declare-a-variable-based-on-your-reusable-class"></a>Aby zadeklarować zmienną na podstawie klasy wielokrotnegoużynia

1. Podczas edytowania okna dialogowego przeciągnij na okno dialogowe formant tego samego typu co klasa podstawowa nowego formantu z paska narzędzi Formanty.

1. Umieść wskaźnik myszy na upuszczonej formancie.

1. Naciskając klawisz CTRL, kliknij dwukrotnie kontrolka.

   Zostanie wyświetlone okno dialogowe [Dodawanie zmiennej elementu](../../ide/add-member-variable-wizard.md) członkowskiego.

1. W polu **Dostęp** wybierz odpowiedni dostęp do formantu.

1. Kliknij pole wyboru **Zmienna sterująca.**

1. W polu **Nazwa zmiennej** wpisz nazwę.

1. W **obszarze Kategoria**kliknij pozycję **Sterowanie**.

1. Na liście **Identyfikator formantu** wybierz formantu, który został dodany. Na liście **Typ zmiennej** powinien być wyświetlany właściwy typ zmiennej, a w polu **Typ formantu** powinien być wyświetlany właściwy typ formantu.

1. W polu **Komentarz** dodaj dowolny komentarz, który ma być wyświetlany w kodzie.

1. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz też

[Mapowanie komunikatów do funkcji](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Dodawanie funkcji elementu członkowskiego](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Dodawanie zmiennej elementu członkowskiego](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Zastępowanie funkcji wirtualnej](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Program obsługi komunikatów MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Poruszanie się po strukturze klasy](../../ide/navigate-code-cpp.md)
