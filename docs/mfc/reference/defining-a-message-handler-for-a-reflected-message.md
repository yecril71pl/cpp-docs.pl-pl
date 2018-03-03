---
title: "Definiowanie obsługi komunikatów dla komunikatów odbitych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.defining.msg.msghandler
dev_langs:
- C++
helpviewer_keywords:
- messages [MFC], reflected
- message handling [MFC], reflected messages
ms.assetid: 5a403528-58c5-46e7-90d5-4a77f0ab9b9c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d9f5e1c472cdbca177b91851f9b8104094c41047
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="defining-a-message-handler-for-a-reflected-message"></a>Definiowanie obsługi komunikatów dla komunikatów odbitych
Po utworzeniu nowej klasie formantów MFC można zdefiniować dla niego obsługi komunikatów. Programy obsługi komunikatów odbitych Zezwalaj Twojej klasy kontrolki do obsługi własnych wiadomości, zanim komunikat jest odbierany przez element nadrzędny. Można używać MFC [CWnd::SendMessage](../../mfc/reference/cwnd-class.md#sendmessage) funkcja do wysyłania wiadomości z formantu do okna nadrzędnego.  
  
 Dzięki tej funkcji, które użytkownik może na przykład utworzyć pole listy, które spowoduje automatyczne odświeżenie zamiast polegania na okno nadrzędne, należy tak (rysowane przez właściciela). Aby uzyskać więcej informacji na komunikaty odbite, zobacz [obsługi wiadomości odzwierciedlone](../../mfc/handling-reflected-messages.md).  
  
 Aby utworzyć [formantu ActiveX](../../mfc/activex-controls-on-the-internet.md) z tą samą funkcjonalnością, należy utworzyć projekt dla formantu ActiveX.  
  
> [!NOTE]
>  Nie można dodać komunikatów odbitych (ocm_ —*komunikat*) w przypadku ActiveX kontroli w oknie właściwości, zgodnie z poniższym opisem. Należy ręcznie dodać tych wiadomości.  
  
### <a name="to-define-a-message-handler-for-a-reflected-message-from-the-properties-window"></a>Aby zdefiniować program obsługi komunikatów dla komunikatów odbitych w oknie właściwości  
  
1.  Dodawanie formantu, takie jak listy, formantu paska pomocniczego, paska narzędzi lub formantem drzewa do projektu MFC.  
  
2.  W widoku klas kliknij nazwę klasy formantu.  
  
3.  W [okna właściwości](/visualstudio/ide/reference/properties-window), nazwą klasy formantu zostanie wyświetlony w **Nazwa klasy** listy.  
  
4.  Kliknij przycisk **wiadomości** przycisk, aby wyświetlić komunikaty systemu Windows, które można dodać do formantu.  
  
5.  Przewiń w dół listę komunikatów w oknie właściwości do momentu wyświetlenia pozycji **Reflected**. Możesz także kliknąć przycisk **kategorii** przycisk i zwijać widok, aby wyświetlić **Reflected** nagłówka.  
  
6.  Wybierz komunikatów odbitych, dla którego chcesz zdefiniować program obsługi. Komunikaty odbite są oznaczone znakiem równości (=).  
  
7.  Kliknij komórkę w prawej kolumnie w oknie właściwości, aby wyświetlić sugerowane nazwę programu obsługi jako \<Dodaj >*HandlerName*. (Na przykład **= wm_ctlcolor —** sugeruje obsługi wiadomości \<Dodaj >**CtlColor**).  
  
8.  Kliknij, aby zaakceptować. Program obsługi zostanie dodany do projektu.  
  
     W prawej kolumnie okna komunikaty odbite są wyświetlane nazwy obsługi komunikatów, które zostały dodane.  
  
9. Aby edytować lub usunąć program obsługi komunikatów, powtórz kroki od 4 do 7. Kliknij komórkę zawierającą nazwę programu obsługi, aby edytować lub usunąć i kliknij odpowiednie zadanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Mapowanie komunikatów na funkcje](../../mfc/reference/mapping-messages-to-functions.md)   
 [Dodawanie funkcji z kreatorami kodów](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)   
 [Dodawanie funkcji członkowskiej](../../ide/adding-a-member-function-visual-cpp.md)   
 [Dodawanie zmiennej członkowskiej](../../ide/adding-a-member-variable-visual-cpp.md)   
 [Zastępowanie funkcji wirtualnych](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Handler komunikatów MFC](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [Nawigacja w strukturze klas](../../ide/navigating-the-class-structure-visual-cpp.md)
