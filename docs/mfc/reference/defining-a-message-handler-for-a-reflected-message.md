---
title: Definiowanie obsługi komunikatów dla komunikatów odbitych
ms.date: 09/07/2019
f1_keywords:
- vc.codewiz.defining.msg.msghandler
helpviewer_keywords:
- messages [MFC], reflected
- message handling [MFC], reflected messages
ms.assetid: 5a403528-58c5-46e7-90d5-4a77f0ab9b9c
ms.openlocfilehash: 1e38c63464cacf445688a1d431a65af21eac86f4
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907941"
---
# <a name="defining-a-message-handler-for-a-reflected-message"></a>Definiowanie obsługi komunikatów dla komunikatów odbitych

Po utworzeniu nowej klasy kontrolki MFC można zdefiniować dla niej obsługę komunikatów. Procedury obsługi komunikatów odbitych pozwalają klasie formantów na obsługę własnych komunikatów przed odebraniem wiadomości przez obiekt nadrzędny. Można użyć funkcji MFC [CWnd:: SendMessage](../../mfc/reference/cwnd-class.md#sendmessage) do wysyłania komunikatów z formantu do okna nadrzędnego.

Korzystając z tej funkcji, możesz na przykład utworzyć pole listy, które zostanie narysowane ponownie, zamiast polegać na oknie nadrzędnym (narysowany przez właściciela). Aby uzyskać więcej informacji na temat komunikatów odbitych, zobacz temat [Obsługa komunikatów odbitych](../../mfc/handling-reflected-messages.md).

Aby utworzyć [kontrolkę ActiveX](../../mfc/activex-controls-on-the-internet.md) o tej samej funkcji, należy utworzyć projekt dla kontrolki ActiveX.

> [!NOTE]
>  Nie można dodać odbicia komunikatu (OCM_*komunikat*) dla kontrolki ActiveX za pomocą kreatora klas, jak opisano poniżej. Te komunikaty należy dodać ręcznie.

### <a name="to-define-a-message-handler-for-a-reflected-message-from-the-class-wizard"></a>Aby zdefiniować procedurę obsługi komunikatów dla wiadomości odbitej z kreatora klas

1. Dodawanie kontrolki, takiej jak lista, kontrolka paska pomocniczego, pasek narzędzi lub kontrolka drzewa, do projektu MFC.

1. W Widok klasy kliknij nazwę klasy formantu.

1. W [Kreatorze klasy](mfc-class-wizard.md)nazwa klasy kontrolki pojawia się na liście **Nazwa klasy** .

1. Kliknij kartę **komunikaty** , aby wyświetlić komunikaty systemu Windows, które są dostępne do dodania do kontrolki.

1. Wybierz komunikat odbity, dla którego chcesz zdefiniować procedurę obsługi. Odzwierciedlone wiadomości są oznaczone znakiem równości (=).

1. Kliknij komórkę w prawej kolumnie w Kreatorze klasy, aby wyświetlić sugerowaną nazwę programu obsługi jako \<dodanie >*procedury obsługi*. (Na przykład program obsługi komunikatów **= WM_CTLCOLOR** sugeruje \<dodanie >**CTLCOLOR**).

1. Kliknij sugerowaną nazwę, która ma zostać zaakceptowana. Procedura obsługi zostanie dodana do projektu.

1. Aby edytować lub usunąć procedurę obsługi komunikatów, powtórz kroki od 4 do 7. Kliknij komórkę zawierającą nazwę programu obsługi, aby edytować lub usunąć i kliknij odpowiednie zadanie.

## <a name="see-also"></a>Zobacz także

[Mapowanie komunikatów do funkcji](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Dodawanie funkcji członkowskiej](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Dodawanie zmiennej członkowskiej](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Zastępowanie funkcji wirtualnej](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Procedura obsługi komunikatów MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Nawigacja w strukturze klas](../../ide/navigate-code-cpp.md)
