---
title: Definiowanie obsługi komunikatów dla komunikatów odbitych
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.defining.msg.msghandler
helpviewer_keywords:
- messages [MFC], reflected
- message handling [MFC], reflected messages
ms.assetid: 5a403528-58c5-46e7-90d5-4a77f0ab9b9c
ms.openlocfilehash: 250d1a838787d1ace682c084bdceeb0e1e6d3c92
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62322998"
---
# <a name="defining-a-message-handler-for-a-reflected-message"></a>Definiowanie obsługi komunikatów dla komunikatów odbitych

Po utworzeniu nowej klasie formantów MFC można zdefiniować programy obsługi komunikatów dla niego. Programy obsługi komunikatów odbitych umożliwiają klasy kontrolki do obsługi własnej komunikaty zanim komunikat jest odbierany przez nadrzędne. Można używać MFC [CWnd::SendMessage](../../mfc/reference/cwnd-class.md#sendmessage) funkcja do wysyłania komunikatów z formantu do okna nadrzędnego.

Dzięki tej funkcji, które można wykonać następujące akcje, na przykład utworzyć pole listy, które spowoduje automatyczne odświeżenie, zamiast polegać na okno nadrzędne zrobić tak (rysowane właściciela). Aby uzyskać więcej informacji na temat komunikaty odbite, zobacz [obsługi wiadomości zostaną uwzględnione](../../mfc/handling-reflected-messages.md).

Aby utworzyć [formantu ActiveX](../../mfc/activex-controls-on-the-internet.md) z taką samą funkcjonalność, należy utworzyć projekt dla formantu ActiveX.

> [!NOTE]
>  Nie można dodać komunikatów odbitych (ocm_ —*komunikat*) w przypadku ActiveX kontroli w oknie właściwości, zgodnie z poniższym opisem. Można ręcznie dodać te komunikaty.

### <a name="to-define-a-message-handler-for-a-reflected-message-from-the-properties-window"></a>Aby zdefiniować program obsługi komunikatów dla komunikatów odbitych z okna właściwości

1. Dodawanie kontrolki, takie jak listy, formantu paska pomocniczego, paska narzędzi lub formantem drzewa do projektu MFC.

1. W widoku klas kliknij nazwę klasy kontrolki.

1. W [okno właściwości](/visualstudio/ide/reference/properties-window), nazwa klasy kontrolki pojawia się w **Nazwa klasy** listy.

1. Kliknij przycisk **wiadomości** przycisk, aby wyświetlić komunikaty Windows dostępnych do dodania do formantu.

1. Przewiń w dół listę komunikatów w oknie dialogowym właściwości, aż zobaczysz nagłówek **Reflected**. Alternatywnie kliknij **kategorie** przycisk i zwijać widok, aby zobaczyć **Reflected** nagłówka.

1. Wybierz komunikatów odbitych, dla którego chcesz zdefiniować program obsługi. Komunikaty odbite są oznaczone znakiem równości (=).

1. Kliknij komórkę w prawej kolumnie w oknie dialogowym właściwości, aby wyświetlić sugerowane nazwę procedury obsługi jako \<Dodaj >*HandlerName*. (Na przykład **= wm_ctlcolor —** sugeruje obsługi wiadomości \<Dodaj >**CtlColor**).

1. Kliknij przycisk sugerowanej nazwy, aby zaakceptować. Program obsługi jest dodawany do projektu.

   W prawej kolumnie w oknie komunikaty odbite są wyświetlane nazwy programów obsługi komunikatów, które zostały dodane.

9. Aby edytować lub usunąć program obsługi komunikatów, powtórz kroki od 4 do 7. Kliknij komórkę zawierającą nazwę programu obsługi w taki sposób, aby edytować lub usunąć i kliknij odpowiednie zadanie.

## <a name="see-also"></a>Zobacz także

[Mapowanie komunikatów do funkcji](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Dodawanie funkcji członkowskiej](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Dodawanie zmiennej członkowskiej](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Zastępowanie funkcji wirtualnych](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Handler komunikatów MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Nawigacja w strukturze klas](../../ide/navigating-the-class-structure-visual-cpp.md)
