---
title: Gdzie można znaleźć mapy komunikatów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- macros, message map
- locating message maps
- message classes [MFC], finding
- message-map macros
ms.assetid: bf59fbc8-b222-42d3-b5d3-0a79aa3cb923
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 19dfaec7d97bed560665fce25c2ddf2cc816a483
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="where-to-find-message-maps"></a>Gdzie można znaleźć mapy komunikatów
Podczas tworzenia nowej aplikacji szkielet przy użyciu Kreatora aplikacji, Kreator aplikacji zapisuje mapy komunikatów dla każdej klasy docelowym polecenia, który tworzy dla Ciebie. W tym aplikacji pochodnej, dokument, widok i klasy okien ramowych. Niektóre z tych mapy komunikatów już wpisy dostarczonych przez Kreatora aplikacji dla niektórych komunikatów i wstępnie zdefiniowanych poleceń i niektóre są tylko symbole zastępcze dla programów obsługi, które mają zostać dodane.  
  
 Mapy wiadomości klasy znajdują się w temacie. Pliku CPP klasy. Praca z mapy komunikatów podstawowe, tworzonych przez Kreatora aplikacji, użyj okna właściwości można dodawać komunikaty i polecenia, które będą obsługiwać każdej klasy. Dodanie niektórych pozycji mapy komunikatów typowe może wyglądać następująco:  
  
 [!code-cpp[NVC_MFCMessageHandling#1](../mfc/codesnippet/cpp/where-to-find-message-maps_1.cpp)]  
  
 Mapy wiadomości składa się z kolekcji makr. Makra dwóch [begin_message_map —](reference/message-map-macros-mfc.md#begin_message_map) i [end_message_map —](reference/message-map-macros-mfc.md#end_message_map), nawiasów mapy komunikatów. Makr, takich jak `ON_COMMAND`, wypełnij zawartości mapy wiadomości.  
  
> [!NOTE]
>  Makra mapy wiadomości nie zostaną wykonane przy użyciu średników.  
  
 Korzystając z Kreatora dodawania klasy do utworzenia nowej klasy, zapewnia mapy komunikatów dla klasy. Alternatywnie można utworzyć mapy komunikatów ręcznie za pomocą edytora kodu źródłowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Jak struktura wyszukuje mapy komunikatów](../mfc/how-the-framework-searches-message-maps.md)

