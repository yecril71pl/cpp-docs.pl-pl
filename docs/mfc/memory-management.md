---
title: "Zarządzanie pamięcią | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- memory [MFC]
- MFC, memory management
- memory allocation [MFC]
- memory [MFC], managing
- memory allocation [MFC], MFC
ms.assetid: 934ac81b-d630-4232-88e5-ea74f7187987
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1a9e31fc1136249f843aa5dc96a4caffcccc7a85
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="memory-management"></a>Zarządzanie pamięcią
Ta grupa artykułów opisuje sposób korzystać z usług ogólnego przeznaczenia z Microsoft Foundation Class biblioteki (MFC) związane z zarządzaniem pamięci. Alokacja pamięci można podzielić na dwie główne kategorie: ramkę alokacji i alokacji sterty.  
  
 Co podstawowa różnica między używane techniki alokacji dwóch polega na tym, że z Alokacja ramek, zwykle pracę z rzeczywistego pamięci zablokowanie, gdy z alokacji sterty są zawsze podany wskaźnik do bloku pamięci. Inny główną różnicą między dwoma systemami jest czy obiekty ramki są automatycznie usuwane, gdy stos obiektów, które muszą zostać jawnie usunięte przez programistę.  
  
 Innego typu niż MFC informacji o pamięci zarządzania programów dla systemu Windows, temacie [zarządzania pamięcią](http://msdn.microsoft.com/library/windows/desktop/aa366779) w zestawie Windows SDK.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Alokacja ramek](../mfc/memory-management-frame-allocation.md)  
  
-   [Alokacja sterty](../mfc/memory-management-heap-allocation.md)  
  
-   [Przydzielanie pamięci dla tablicy](../mfc/memory-management-examples.md)  
  
-   [Cofanie przydziału pamięci dla tablicy w stercie](../mfc/memory-management-examples.md)  
  
-   [Przydzielanie pamięci dla struktury danych](../mfc/memory-management-examples.md)  
  
-   [Przydzielanie pamięci dla obiektu](../mfc/memory-management-examples.md)  
  
-   [Bloki pamięci o zmiennych rozmiarach](../mfc/memory-management-resizable-memory-blocks.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia](../mfc/mfc-concepts.md)   
 [Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)

