---
title: 'Aktywacja: Zlecenia | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- verbs [MFC]
- OLE [MFC], activation
- edit verb [MFC]
- activation [MFC], verbs
- OLE [MFC], editing
- Primary verb [MFC]
- OLE activation {MFC]
ms.assetid: eb56ff23-1de8-43ad-abeb-dc7346ba7b70
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c2a443f4ce65dcc7e9460bd016638aa5069e7e6d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="activation-verbs"></a>Aktywacja: zlecenia
W tym artykule opisano play zleceń podstawowych i pomocniczych roli w OLE [aktywacji](../mfc/activation-cpp.md).  
  
 Zwykle kliknij dwukrotnie element osadzony umożliwia użytkownikowi go edytować. Jednak niektóre elementy nie działają w ten sposób. Na przykład dwukrotne kliknięcie utworzone za pomocą aplikacji Rejestrator dźwięku nie otworzyć serwer w osobnym oknie; Zamiast tego odtwarza dźwięk.  
  
 Przyczyna tej różnicy zachowanie to, czy Rejestrator dźwięku elementy mają różne "primary — zlecenie." Primary — zlecenie jest Akcja podejmowana, gdy użytkownik kliknie dwukrotnie element OLE. Dla większości elementów OLE primary — zlecenie jest edycji, który uruchamia serwer, który utworzył element. W przypadku niektórych typów elementów, takich jak elementy Rejestrator dźwięku primary — zlecenie jest Play.  
  
 Wiele typów elementów OLE obsługuje tylko jedno zlecenie i edycja jest najczęściej. Jednak niektóre typy elementów obsługuje wiele zleceń. Na przykład Rejestrator dźwięku obsługuje elementy edytować jako dodatkowej zlecenia.  
  
 Zlecenie innego często używane jest otwarty. Otwórz zlecenie jest identyczny edycji, z wyjątkiem aplikacja jest uruchamiana w oddzielnym oknie. Jeśli aplikacja kontenera lub aplikacji serwera nie obsługuje aktywacji w miejscu, należy użyć tego zlecenia.  
  
 Wszystkie zlecenia innego niż podstawowy zlecenie muszą być wywoływane za pomocą polecenia podmenu, gdy zaznaczony element. To podmenu zawiera wszystkie zlecenia, które są obsługiwane przez element i zwykle jest osiągalny *typename* **obiektu** na **Edytuj** menu. Aby uzyskać informacje dotyczące *typename* **obiektu** polecenia, zobacz artykuł [menu i zasoby: dodatki do kontenera](../mfc/menus-and-resources-container-additions.md).  
  
 Zlecenia, który obsługuje aplikacja serwera są wyświetlane w bazie danych rejestracji systemu Windows. Jeśli aplikacja serwera są zapisywane z Microsoft Foundation Class Library, automatycznie zarejestrować wszystkie zlecenia, gdy serwer jest uruchomiony. Jeśli nie, należy je zarejestrować w fazie inicjowania aplikacji serwera. Aby uzyskać więcej informacji, zobacz artykuł [rejestracji](../mfc/registration.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Aktywacji](../mfc/activation-cpp.md)   
 [Kontenery](../mfc/containers.md)   
 [Serwery](../mfc/servers.md)

