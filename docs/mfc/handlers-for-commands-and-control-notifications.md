---
title: "Programy obsługi dla poleceń i powiadomień dotyczących formantu karty | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- commands [MFC], handlers for
- functions [MFC], handler
- handlers [MFC]
- controls [MFC], notifications
- handlers [MFC], control notification [MFC]
- notifications [MFC], handlers for control
- handlers [MFC], command
ms.assetid: 20f57f4a-f577-4c09-80a2-43faf32a1c2e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c4846b94a03eb24e1fca8f7e802f4019e0ebaea1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="handlers-for-commands-and-control-notifications"></a>Programy obsługi dla poleceń i powiadomień dotyczących formantów
Nie ma żadnych domyślne programy obsługi poleceń lub komunikaty powiadomień dotyczących formantu. W związku z tym są powiązane tylko przez Konwencję w nazewnictwa programu obsługi dla tych kategorii wiadomości. Podczas mapowania powiadomień polecenie lub formant do programu obsługi, okna właściwości zaproponuje nazwę na podstawie kodu polecenia Identyfikatora lub powiadomień dotyczących formantu. Można zaakceptować proponowana nazwa, zmień go lub go zastąpić.  
  
 Konwencja sugeruje nazw programy obsługi zdarzeń w obu kategorii dla obiekt interfejsu użytkownika, które reprezentują. W związku z tym program obsługi poleceń Wytnij menu Edycja może mieć nazwę.  
  
 [!code-cpp[NVC_MFCMessageHandling#4](../mfc/codesnippet/cpp/handlers-for-commands-and-control-notifications_1.h)]  
  
 Ponieważ polecenia Wytnij tak często jest zaimplementowana w aplikacjach, platformę powoduje wstępne definiowanie identyfikator polecenia dla polecenia Wytnij jako **id_edit_cut —**. Aby uzyskać listę wszystkich poleceń wstępnie zdefiniowane identyfikatory Zobacz plik AFXRES. H. Aby uzyskać więcej informacji, zobacz [standardowych poleceń](../mfc/standard-commands.md).  
  
 Ponadto Konwencji sugeruje obsługi dla **BN_CLICKED** komunikatu powiadomienia z przycisku "Moje Button" może mieć nazwę.  
  
 [!code-cpp[NVC_MFCMessageHandling#5](../mfc/codesnippet/cpp/handlers-for-commands-and-control-notifications_2.h)]  
  
 To polecenie może przypisywać identyfikator `IDC_MY_BUTTON` , ponieważ jest to równoważne obiektu interfejsu użytkownika specyficzne dla aplikacji.  
  
 Obu rodzajów wiadomości nie przyjmują argumentów i zwraca żadnej wartości.  
  
## <a name="see-also"></a>Zobacz też  
 [Deklarowanie funkcji obsługi komunikatów](../mfc/declaring-message-handler-functions.md)
