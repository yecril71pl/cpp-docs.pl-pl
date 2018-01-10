---
title: "Schowek: Dodawanie innych formatów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- formats [MFC], Clipboard
- Clipboard, formats
- custom formats, placing on Clipboard
- custom formats
- registering custom Clipboard data formats
- custom Clipboard data formats
ms.assetid: aea58159-65ed-4385-aeaa-3d9d5281903b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6e6f7f21a64c062e2f210be9f13ce04428c397f9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="clipboard-adding-other-formats"></a>Schowek: dodawanie innych formatów
W tym temacie wyjaśniono, jak i rozwiń listę obsługiwanych formatów, szczególnie w przypadku obsługi. Temat [Schowek: kopiowanie i wkleić danych](../mfc/clipboard-copying-and-pasting-data.md) opisuje minimalne wykonania niezbędnych do obsługi kopiowanie i wklejanie ze Schowka. Jeśli to wszystkie zaimplementowaniem tylko formaty w Schowku znajduje są `CF_METAFILEPICT`, **CF_EMBEDSOURCE**, **CF_OBJECTDESCRIPTOR**i prawdopodobnie `CF_LINKSOURCE`. Większości aplikacji potrzebna jest więcej formatów w Schowku niż tych trzech.  
  
##  <a name="_core_registering_custom_formats"></a>Rejestrowanie niestandardowe formaty  
 Aby utworzyć własne niestandardowe formaty, wykonaj tę samą procedurę, należy użyć podczas rejestrowania dowolnego niestandardowego formatu Schowka: przekazywania nazwy formatu **RegisterClipboardFormat** funkcji i używać jej wartości zwracany jako identyfikator formatu.  
  
##  <a name="_core_placing_formats_on_the_clipboard"></a>Wprowadzenie do formatów w Schowku  
 Aby dodać więcej formatów w Schowku znajduje, konieczne jest przesłonięcie `OnGetClipboardData` funkcji klasy pochodne albo `COleClientItem` lub `COleServerItem` (w zależności od tego, czy dane do skopiowania jest natywny). W tej funkcji należy użyć następującej procedury.  
  
#### <a name="to-place-formats-on-the-clipboard"></a>Formaty do Schowka  
  
1.  Utwórz `COleDataSource` obiektu.  
  
2.  Przekazywanie tego źródła danych do funkcji, która dodaje z formatów danych natywnych do listy obsługiwanych formatów przez wywołanie metody `COleDataSource::CacheGlobalData`.  
  
3.  Dodawanie standardowych formatów przez wywołanie metody `COleDataSource::CacheGlobalData` dla każdego standardowego formatu, które mają być obsługiwane.  
  
 Ta metoda jest używana w programie MFC OLE próbki [HIERSVR](../visual-cpp-samples.md) (Sprawdź `OnGetClipboardData` funkcji członkowskiej klasy **CServerItem** klasy). Jedyną różnicą w tym przykładzie jest tego kroku trzech nie jest zaimplementowana, ponieważ HIERSVR obsługuje nie standardowych formatów.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Źródła danych OLE obiekty i dane oraz uniform transferów danych](../mfc/data-objects-and-data-sources-ole.md)  
  
-   [Przeciąganie i upuszczanie OLE](../mfc/drag-and-drop-ole.md)  
  
-   [OLE](../mfc/ole-background.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Schowek: korzystanie z mechanizmu schowka OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)

