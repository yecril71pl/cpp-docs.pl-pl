---
title: "Dodawanie obsługi ATL komunikat | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- message handlers [C++]
- ATL, windows
- message handling [C++], ATL message handler
- windows [C++], ATL
- ATL, message handlers
ms.assetid: cdea38a1-0d9b-4f8d-bbd5-b4f063fb3eeb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4358dc54589971c559bec48adf77252d4f4cda28
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="adding-an-atl-message-handler"></a>Dodawanie obsługi ATL wiadomości
Aby dodać program obsługi komunikatów (funkcję elementu członkowskiego, która obsługuje komunikatów systemu Windows) do formantu, należy najpierw wybrać formant w widoku klas. Następnie otwórz **właściwości** wybierz **wiadomości** ikonę, a następnie kliknij przycisk, kontrolować listy rozwijanej w polu obok komunikatu wymagane. Spowoduje to dodanie deklaracji dla obsługi wiadomości w pliku nagłówka formantu i szkielet implementację programu obsługi w pliku .cpp formantu. Zostanie również dodać mapy wiadomości i Dodaj wpis dla programu obsługi.  
  
 Dodawanie obsługi wiadomości w ATL jest podobne do dodawania obsługi wiadomości do klasy MFC. Zobacz [Dodawanie Handlera komunikatów MFC](../mfc/reference/adding-an-mfc-message-handler.md) Aby uzyskać więcej informacji.  
  
 Tylko na dodawanie obsługi ATL wiadomości mają zastosowanie następujące warunki:  
  
-   Programy obsługi wiadomości postępuj zgodnie z tej samej konwencji nazewnictwa jak MFC.  
  
-   Nowe wpisy mapy wiadomości są dodawane do mapy komunikatów głównego. Kreator nie może rozpoznać mapy komunikatów alternatywny i łańcucha.  
  
## <a name="see-also"></a>Zobacz też  
 [Implementowanie okna](../atl/implementing-a-window.md)

