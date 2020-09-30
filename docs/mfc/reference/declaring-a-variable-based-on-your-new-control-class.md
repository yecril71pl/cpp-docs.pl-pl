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
ms.openlocfilehash: a828351a9e789228143d43d4c0a756abda879989
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506682"
---
# <a name="declaring-a-variable-based-on-your-new-control-class"></a>Deklarowanie zmiennej opartej na nowej klasie formantów

Po utworzeniu klasy formantów MFC można zadeklarować zmienną na podstawie jej. Aby zapewnić kontekst dla nowej zmiennej, należy otworzyć Edytor okna dialogowego i edytować okno dialogowe, w którym ma być używana kontrolka wielokrotnego użytku. Ponadto do okna dialogowego musi już być skojarzona Klasa. Aby uzyskać informacje na temat korzystania z edytora okien dialogowych, zobacz [Edytor okien dialogowych](../../windows/dialog-editor.md).

### <a name="to-declare-a-variable-based-on-your-reusable-class"></a>Aby zadeklarować zmienną na podstawie klasy wielokrotnego użytku

1. Podczas edytowania okna dialogowego przeciągnij kontrolkę tego samego typu co Klasa bazowa nowej kontrolki na pasku narzędzi kontrolek do okna dialogowego.

1. Umieść wskaźnik myszy nad porzuconym formantem.

1. Podczas naciskania klawisza CTRL, kliknij dwukrotnie formant.

   Zostanie wyświetlone okno dialogowe [Dodawanie zmiennej członkowskiej](../../ide/adding-a-member-variable-visual-cpp.md#add-member-variable-wizard) .

1. W polu **dostęp** wybierz odpowiedni dostęp dla kontrolki.

1. Kliknij pole wyboru **zmienna kontroli** .

1. W polu **Nazwa zmiennej** wpisz nazwę.

1. W obszarze **Kategoria**kliknij pozycję **Kontrola**.

1. Z listy **Identyfikator formantu** Wybierz dodaną kontrolkę. Na liście **Typ zmiennej** powinna być wyświetlana poprawna wartość typu zmiennej, a w polu **Typ formantu** powinien być wyświetlany poprawny typ formantu.

1. W polu **komentarz** Dodaj dowolny komentarz, który ma być wyświetlany w kodzie.

1. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz też

[Mapowanie komunikatów do funkcji](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Dodawanie funkcji członkowskiej](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Dodawanie zmiennej członkowskiej](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Zastępowanie funkcji wirtualnej](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Procedura obsługi komunikatów MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Nawigacja w strukturze klas](../../ide/navigate-code-cpp.md)
