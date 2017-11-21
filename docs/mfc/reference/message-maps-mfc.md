---
title: Komunikat map (MFC) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.messages
dev_langs: C++
helpviewer_keywords:
- message maps [MFC], MFC
- Windows messages [MFC], message maps
- messages [MFC], Windows
- MFC, messages
ms.assetid: 3f9855e4-9d7d-4b64-8f3f-a19ea3cf79ba
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 677a4a06402af1115f419dcd5979a13a84d79e08
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="message-maps-mfc"></a>Mapy komunikatów (MFC)
Ta sekcja dokumentacji Wyświetla listę wszystkich [makra mapowania wiadomości](../../mfc/reference/message-map-macros-mfc.md) i wszystkie [CWnd](../../mfc/reference/cwnd-class.md) prototypy funkcji wpisy mapy wiadomości wraz z odpowiadającego mu członka:  
  
|Kategoria|Opis|  
|--------------|-----------------|  
|ON\_polecenie obsługi wiadomości|Obsługuje `WM_COMMAND` komunikaty generowane przez użytkownika opcji menu lub menu klucze dostępu.|  
|[Programy obsługi komunikatów powiadomień okna podrzędnego](../../mfc/reference/child-window-notification-message-handlers.md)|Obsługa komunikatów powiadomień z okien podrzędnych.|  
|[Programy obsługi komunikatów WM_](../../mfc/reference/handlers-for-wm-messages.md)|Obsługa `WM_` komunikaty, takie jak `WM_PAINT`.|  
|[Programy obsługi komunikatów zdefiniowanych przez użytkownika](../../mfc/reference/user-defined-handlers.md)|Obsługa wiadomości zdefiniowane przez użytkownika.|  
  
 (Aby uzyskać informacje o terminologii i konwencje użytego w niniejszej dokumentacji, zobacz [jak używanie odsyłacza mapy komunikatów](../../mfc/reference/how-to-use-the-message-map-cross-reference.md).)  
  
 Od systemu Windows to system operacyjny przesyłania wiadomości, duża część programowania w języku środowiska systemu Windows obejmuje obsługi wiadomości. Występuje zawsze kliknij zdarzenie, takich jak naciśnięcie klawisza lub mysz, wiadomości są wysyłane do aplikacji, która następnie musi obsługiwać zdarzenia.  
  
 Microsoft Foundation Class Library zapewnia model programowania zoptymalizowane pod kątem Programowanie oparte na wiadomość. W tym modelu "mapy komunikatów" służą do wyznaczenia, które funkcje obsługi różnych wiadomości dla określonej klasy. Mapy komunikatów zawiera co najmniej jeden makra, które określają wiadomości, które będzie obsługiwany przez funkcje, które. Na przykład komunikat mapy zawierający `ON_COMMAND` makro może wyglądać mniej więcej tak:  
  
 [!code-cpp[NVC_MFCMessageMaps#16](../../mfc/reference/codesnippet/cpp/message-maps-mfc_1.cpp)]  
  
 `ON_COMMAND` Makro jest używane do obsługi polecenia komunikaty generowane przez menu, przycisków i klawiszy skrótów. [Makra](../../mfc/reference/message-map-macros-mfc.md) są dostępne następujące mapowania:  
  
## <a name="windows-messages"></a>Komunikaty systemu Windows  
  
-   Powiadomień dotyczących formantu karty  
  
-   Zdefiniowane przez użytkownika wiadomości  
  
## <a name="command-messages"></a>Komunikaty poleceń  
  
-   Zarejestrowany wiadomości zdefiniowane przez użytkownika  
  
-   Interfejs użytkownika aktualizacji wiadomości  
  
## <a name="ranges-of-messages"></a>Zakresy wiadomości  
  
-   Polecenia  
  
-   Aktualizacja programu obsługi wiadomości  
  
-   Powiadomień dotyczących formantu karty  
  
 Makra mapy wiadomości są ważne, zwykle nie trzeba ich używać bezpośrednio. Jest to spowodowane okna właściwości automatycznie tworzy wpisy mapy wiadomości w plikach źródłowych przypadku użycia jej do skojarzenia z komunikatami funkcji obsługi wiadomości. Zawsze, gdy chcesz edytować lub dodanie wpisu mapy wiadomości, można użyć okna właściwości.  
  
> [!NOTE]
>  Okno właściwości nie obsługuje zakresów map komunikatów. Musisz zapisać te wpisy mapy wiadomości samodzielnie.  
  
 Mapy komunikatów są jednak ważnym elementem Microsoft Foundation Class Library. Należy się dowiedzieć, co robią, i dokumentacja jest dostępna dla nich.  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

