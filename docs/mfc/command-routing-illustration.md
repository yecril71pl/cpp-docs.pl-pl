---
title: Ilustracja routingu poleceń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, command routing
- command handling [MFC], routing commands
- command routing [MFC], OnCmdMsg handler
ms.assetid: 4b7b4741-565f-4878-b076-fd85c670f87f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a12a5cd19177761dfbf484c64f528d8def194ca5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341139"
---
# <a name="command-routing-illustration"></a>Ilustracja routingu poleceń
Aby zilustrować, należy wziąć pod uwagę komunikatem polecenia z elementu menu Wyczyść wszystko w menu Edycja aplikacji MDI. Załóżmy, że funkcja obsługi dla tego polecenia stanie się być funkcją członkowską klasy dokumentów aplikacji. Oto, jak polecenie osiągnie jej procedura obsługi po wybraniu elementu menu:  
  
1.  Głównego okna ramowego najpierw odbiera komunikat polecenia.  
  
2.  Główne okno ramowe MDI daje aktywnego okna podrzędnego MDI możliwość obsługi polecenia.  
  
3.  Standardowy routing ramki okna podrzędnego MDI przedstawia swoją opinię stosowany w wierszu polecenia przed sprawdzaniem własny mapy komunikatów.  
  
4.  Widok najpierw sprawdza własną mapy komunikatów i wyszukiwanie bez obsługi obok kieruje polecenia do jego skojarzonego dokumentu.  
  
5.  Dokument sprawdza jego mapę komunikatów i wyszukuje obsługi. Ta funkcja elementu członkowskiego dokumentu jest wywoływana i zatrzymuje routingu.  
  
 Jeśli dokument nie ma obsługi, go polecenie będzie dalej trasy do jego szablonu dokumentu. Następnie polecenie zwróci się do widoku, a następnie okno ramowe. Ponadto okno ramowe czy sprawdź jego mapy komunikatów. Jeśli sprawdzanie również zakończyło się niepowodzeniem, polecenia zostanie przekierowane do głównego okna MDI ramki, a następnie do obiektu aplikacji — ultimate docelowego nieobsługiwanych poleceń.  
  
## <a name="see-also"></a>Zobacz też  
 [Jak struktura wywołuje programy obsługi](../mfc/how-the-framework-calls-a-handler.md)

