---
title: Dodawanie obsługi ATL komunikat | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message handlers [C++]
- ATL, windows
- message handling [C++], ATL message handler
- windows [C++], ATL
- ATL, message handlers
ms.assetid: cdea38a1-0d9b-4f8d-bbd5-b4f063fb3eeb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e79598b79ccbad13ad98c7fc1284808fe1b05cfc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="adding-an-atl-message-handler"></a>Dodawanie obsługi ATL wiadomości
Aby dodać program obsługi komunikatów (funkcję elementu członkowskiego, która obsługuje komunikatów systemu Windows) do formantu, należy najpierw wybrać formant w widoku klas. Następnie otwórz **właściwości** wybierz **wiadomości** ikonę, a następnie kliknij przycisk, kontrolować listy rozwijanej w polu obok komunikatu wymagane. Spowoduje to dodanie deklaracji dla obsługi wiadomości w pliku nagłówka formantu i szkielet implementację programu obsługi w pliku .cpp formantu. Zostanie również dodać mapy wiadomości i Dodaj wpis dla programu obsługi.  
  
 Dodawanie obsługi wiadomości w ATL jest podobne do dodawania obsługi wiadomości do klasy MFC. Zobacz [Dodawanie Handlera komunikatów MFC](../mfc/reference/adding-an-mfc-message-handler.md) Aby uzyskać więcej informacji.  
  
 Tylko na dodawanie obsługi ATL wiadomości mają zastosowanie następujące warunki:  
  
-   Programy obsługi wiadomości postępuj zgodnie z tej samej konwencji nazewnictwa jak MFC.  
  
-   Nowe wpisy mapy wiadomości są dodawane do mapy komunikatów głównego. Kreator nie może rozpoznać mapy komunikatów alternatywny i łańcucha.  
  
## <a name="see-also"></a>Zobacz też  
 [Implementowanie okna](../atl/implementing-a-window.md)

