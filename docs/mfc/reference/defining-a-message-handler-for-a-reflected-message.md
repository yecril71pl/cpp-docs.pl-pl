---
title: Definiowanie obsługi komunikatów dla komunikatów odbitych
ms.date: 09/07/2019
f1_keywords:
- vc.codewiz.defining.msg.msghandler
helpviewer_keywords:
- messages [MFC], reflected
- message handling [MFC], reflected messages
ms.assetid: 5a403528-58c5-46e7-90d5-4a77f0ab9b9c
ms.openlocfilehash: f7f90d3347ac61abcfcb48e77ef39aa2626ae5c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365857"
---
# <a name="defining-a-message-handler-for-a-reflected-message"></a>Definiowanie obsługi komunikatów dla komunikatów odbitych

Po utworzeniu nowej klasy kontroli MFC, można zdefiniować programy obsługi wiadomości dla niego. Programy obsługi komunikatów odzwierciedlenie pozwalają klasy kontroli do obsługi własnych wiadomości przed odebraniem wiadomości przez element nadrzędny. Za pomocą funkcji MFC [CWnd::SendMessage](../../mfc/reference/cwnd-class.md#sendmessage) można wysyłać wiadomości z formantu do okna nadrzędnego.

Dzięki tej funkcji można na przykład utworzyć pole listy, które będzie przerysowywać się, a nie polegać na oknie nadrzędnym, aby to zrobić (narysowany właściciel). Aby uzyskać więcej informacji na temat wiadomości odbitych, zobacz [Obsługa wiadomości odzwierciedlenie](../../mfc/handling-reflected-messages.md).

Aby utworzyć [formant ActiveX](../../mfc/activex-controls-on-the-internet.md) z tą samą funkcją, należy utworzyć projekt dla formantu ActiveX.

> [!NOTE]
> Nie można dodać odbitej wiadomości (OCM_*Message)* dla formantu ActiveX za pomocą Kreatora klas, jak opisano poniżej. Należy dodać te wiadomości ręcznie.

### <a name="to-define-a-message-handler-for-a-reflected-message-from-the-class-wizard"></a>Aby zdefiniować program obsługi wiadomości dla odbitej wiadomości z Kreatora klas

1. Dodaj formant, takich jak lista, zbrojenia, pasek narzędzi lub formant drzewa, do projektu MFC.

1. W widoku klasy kliknij nazwę klasy kontrolnej.

1. W [Kreatorze klas](mfc-class-wizard.md)nazwa klasy jest wyświetlana na liście **Nazwa klasy.**

1. Kliknij kartę **Wiadomości,** aby wyświetlić komunikaty systemu Windows dostępne do dodania do formantu.

1. Wybierz odbitą wiadomość, dla której chcesz zdefiniować program obsługi. Odbite wiadomości są oznaczone znakiem równości (=).

1. Kliknij komórkę w prawej kolumnie Kreatora klas, aby \<wyświetlić sugerowaną nazwę programu obsługi jako dodaj>*HandlerName*. (Na przykład **program** obsługi wiadomości =WM_CTLCOLOR \<sugeruje dodanie>**CtlColor**).

1. Kliknij sugerowaną nazwę, aby zaakceptować. Program obsługi jest dodawany do projektu.

1. Aby edytować lub usunąć program obsługi wiadomości, powtórz kroki od 4 do 7. Kliknij komórkę zawierającą nazwę programu obsługi, aby edytować lub usunąć i kliknij odpowiednie zadanie.

## <a name="see-also"></a>Zobacz też

[Mapowanie komunikatów do funkcji](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Dodawanie funkcji elementu członkowskiego](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Dodawanie zmiennej elementu członkowskiego](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Zastępowanie funkcji wirtualnej](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Program obsługi komunikatów MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Poruszanie się po strukturze klasy](../../ide/navigate-code-cpp.md)
