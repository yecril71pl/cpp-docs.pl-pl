---
title: "Dodawanie funkcji do formantu złożonego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- event handlers [C++], ActiveX controls
- composite controls, handling events
- ActiveX controls [C++], events
ms.assetid: 98f85681-9564-480d-af38-03f9733fe58b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7282ba7eb80fd30175751bb5234818a5e3cf1431
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="adding-functionality-to-the-composite-control"></a>Dodawanie funkcji do złożonych kontrolek
Po wstawieniu niezbędnej kontroli do formantu złożonego następny krok polega na dodawanie nowych funkcji. Ta nowa funkcja zazwyczaj znajduje się na dwie kategorie:  
  
-   Pomocnicze dodatkowe interfejsy i dostosowywanie zachowania użytkownika formantu złożonego za pomocą funkcji dodatkowych, określonych.  
  
-   Obsługa zdarzeń z formantu ActiveX zawartych w niej (lub kontrolki).  
  
 Cel i zakres tego artykułu w pozostałej części tej sekcji przedstawiono wyłącznie Obsługa zdarzeń z kontrolki ActiveX.  
  
> [!NOTE]
>  Jeśli wymagana jest obsługa komunikatów z formantów systemu Windows, zobacz [implementacji okna](../atl/implementing-a-window.md) uzyskać więcej informacji na temat obsługi w ATL. wiadomości  
  
 Po wstawieniu formantu ActiveX w zasobu okna dialogowego, kliknij prawym przyciskiem myszy formantu, a następnie kliknij przycisk **Dodaj program obsługi zdarzeń**. Wybierz zdarzenie, aby obsłużyć, a następnie kliknij przycisk **dodawać i edytować**. Kod obsługi zdarzenia zostaną dodane do pliku .h formantu.  
  
 Punkty połączenia dla formantów ActiveX formantu złożonego są automatycznie podłączone i odłączone za pośrednictwem wywołania [CComCompositeControl::AdviseSinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap).  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawy złożonych kontrolek](../atl/atl-composite-control-fundamentals.md)

