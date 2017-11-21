---
title: "Przeciąganie i upuszczanie: dostosowywanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- drag and drop [MFC], implementing in non-OLE applications
- drag and drop [MFC], customizing behavior
- drag and  [MFC], COleDataSource object
- drag and drop [MFC], calling DoDragDrop
- OLE drag and drop [MFC], customizing behavior
ms.assetid: 03369d3e-46bf-4140-b58c-d0c9657cf38a
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 71d0060866b6a02de3c58ed40100dee59743749b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="drag-and-drop-customizing"></a>Przeciąganie i upuszczanie: dostosowywanie
Domyślna implementacja funkcji przeciągania i upuszczania jest odpowiednia dla większości aplikacji. Jednak niektóre aplikacje mogą wymagać, że można zmienić to zachowanie standardowego. W tym artykule opisano kroki niezbędne zmienić te ustawienia domyślne. Ponadto można użyć tej metody ustanowienie aplikacje, które nie obsługują dokumenty złożone jako źródła listy.  
  
 Jeśli dostosowywania standardowe zachowanie przeciąganie i upuszczanie OLE lub aplikacji innych niż OLE, należy utworzyć `COleDataSource` obiekt zawierający dane. Gdy użytkownik uruchomi operacji przeciągania i upuszczania, kod powinien wywoływać `DoDragDrop` funkcji z tego obiektu, a nie z innych klas, które obsługują operacje przeciągania i upuszczania.  
  
 Opcjonalnie możesz utworzyć `COleDropSource` obiekt, aby kontrolować usuwania i zastępowania niektórych jej funkcji, w zależności od typu zachowania, które chcesz zmienić. Ten obiekt źródło porzucenia są następnie przekazywane do `COleDataSource::DoDragDrop` Aby zmienić domyślne zachowanie tych funkcji. Opcji Zezwalaj na dużą elastyczność w sposób obsługi operacji przeciągania i upuszczania w aplikacji. Aby uzyskać więcej informacji na temat źródeł danych, zobacz artykuł [obiekty danych i źródła danych (OLE)](../mfc/data-objects-and-data-sources-ole.md).  
  
 Można zastąpić następujące funkcje, aby dostosować operacji przeciągania i upuszczania:  
  
|Zastąpienie|Aby dostosować|  
|--------------|------------------|  
|`OnBeginDrag`|Jak przeciąganie jest inicjowana po wywołaniu metody `DoDragDrop`.|  
|`GiveFeedback`|Wizualne, takie jak wyglądem kursora dla różnych listy wyników.|  
|`QueryContinueDrag`|Zakończenie operacji przeciągania i upuszczania. Ta funkcja umożliwia sprawdzenie modyfikator stanów klucza podczas operacji przeciągania.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przeciąganie i upuszczanie (OLE)](../mfc/drag-and-drop-ole.md)   
 [Klasa COleDropSource](../mfc/reference/coledropsource-class.md)   
 [COleDataSource — klasa](../mfc/reference/coledatasource-class.md)
