---
title: 'Serwery: Implementowanie okien ramowych w miejscu | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- frame windows [MFC], implementing
- OLE server applications [MFC], frame windows
- servers, in-place frame windows
- frame windows [MFC], in-place
- in-place frame windows
ms.assetid: 09bde4d8-15e2-4fba-8d14-9b954d926b92
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7e26cbb0099f897c65ab3e39338f3c36e77112e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="servers-implementing-in-place-frame-windows"></a>Serwery: implementowanie okien ramowych w miejscu
W tym artykule opisano, co należy zrobić, aby zaimplementować okna ramowe w miejscu w visual edytowania aplikacji serwera, jeśli nie używasz Kreatora aplikacji do tworzenia aplikacji serwera. Zamiast zgodnie z procedurą przedstawioną w tym artykule, można użyć istniejącej klasy okien ramowych w miejscu z aplikacją generowane przez Kreatora aplikacji lub próbkę dostarczone z programem Visual C++.  
  
#### <a name="to-declare-an-in-place-frame-window-class"></a>Aby zadeklarować klasy okien ramowych w miejscu  
  
1.  Klasy okien ramowych w miejscu z pochodzi `COleIPFrameWnd`.  
  
    -   Użyj `DECLARE_DYNCREATE` makra w pliku nagłówka klasy.  
  
    -   Użyj `IMPLEMENT_DYNCREATE` makra w pliku implementacji (.cpp) klasy. Dzięki temu obiektów tej klasy, które ma zostać utworzony przez platformę.  
  
2.  Deklarowanie `COleResizeBar` elementu członkowskiego klasy okien ramowych. Jest to niezbędne, jeśli mają być obsługiwane w aplikacjach server zmiany rozmiaru w miejscu.  
  
     Zadeklaruj `OnCreate` obsługi wiadomości (przy użyciu **właściwości** okna) i Wywołaj **Utwórz** dla Twojej `COleResizeBar` elementu członkowskiego, jeśli go.  
  
3.  Jeśli masz paska narzędzi zadeklarować `CToolBar` elementu członkowskiego klasy okien ramowych.  
  
     Zastąpienie `OnCreateControlBars` funkcji członkowskiej można utworzyć paska narzędzi, gdy serwer jest aktywny w miejscu. Na przykład:  
  
     [!code-cpp[NVC_MFCOleServer#1](../mfc/codesnippet/cpp/servers-implementing-in-place-frame-windows_1.cpp)]  
  
     Zawiera omówienie ten kod następujący krok 5.  
  
4.  W pliku .cpp głównego, należy umieścić plik nagłówka dla tej klasy okien ramowych w miejscu.  
  
5.  W `InitInstance` dla klasy aplikacji, należy wywołać `SetServerInfo` funkcji obiektu szablonu dokumentu do określania zasobów i okno ramowe w miejscu do użycia w otwarte i w miejscu do edycji.  
  
 Wywołuje szereg funkcji w **Jeśli** instrukcja tworzy pasek narzędzi z zasobów podany serwer. W tym momencie pasek narzędzi jest częścią hierarchii okna kontenera. Ponieważ ten pasek narzędzi jest pochodną `CToolBar`, go przekazuje jego wiadomości do jego właściciel, okno ramowe aplikacji kontenera, chyba że zmienić właściciela. Dlatego wywołanie `SetOwner` jest konieczne. To wywołanie zmienia okna, gdy polecenia są wysyłane jako okno ramowe w miejscu serwera, powodując wiadomości, które mają być przekazane do serwera. Dzięki temu serwer zareagować na operacje na pasku narzędzi, który zapewnia.  
  
 Identyfikator mapy bitowej narzędzi powinien być taki sam jak inne zasoby w miejscu zdefiniowanych w aplikacji serwera. Zobacz [menu i zasoby: dodatki do serwera](../mfc/menus-and-resources-server-additions.md) szczegółowe informacje.  
  
 Aby uzyskać więcej informacji, zobacz [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md), [COleResizeBar](../mfc/reference/coleresizebar-class.md), i [CDocTemplate::SetServerInfo](../mfc/reference/cdoctemplate-class.md#setserverinfo) w *informacje dotyczące biblioteki klas*.  
  
## <a name="see-also"></a>Zobacz też  
 [Serwery](../mfc/servers.md)   
 [Serwery: Implementowanie serwera](../mfc/servers-implementing-a-server.md)   
 [Serwery: Implementowanie dokumentów serwera](../mfc/servers-implementing-server-documents.md)   
 [Serwery: elementy serwera](../mfc/servers-server-items.md)

