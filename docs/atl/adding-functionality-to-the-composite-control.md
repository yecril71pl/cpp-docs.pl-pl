---
title: Dodawanie funkcji do formantu złożonego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- event handlers [C++], ActiveX controls
- composite controls, handling events
- ActiveX controls [C++], events
ms.assetid: 98f85681-9564-480d-af38-03f9733fe58b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 67602e16fc5a30c82e82772b6b9f6c553ba79d9b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32354185"
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

