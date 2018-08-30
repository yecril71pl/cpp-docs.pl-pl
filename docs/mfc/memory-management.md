---
title: Zarządzanie pamięcią | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- memory [MFC]
- MFC, memory management
- memory allocation [MFC]
- memory [MFC], managing
- memory allocation [MFC], MFC
ms.assetid: 934ac81b-d630-4232-88e5-ea74f7187987
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 28191191572e508828a23f0e719a57d63163b08d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43222354"
---
# <a name="memory-management"></a>Zarządzanie pamięcią
Ta grupa artykułów opisano, jak korzystać z usług ogólnego przeznaczenia z Microsoft Foundation Class Library (MFC) związane z zarządzaniem pamięcią. Alokacja pamięci można podzielić na dwie główne kategorie: klatki, alokacji i Alokacje sterty.  
  
 Jedną z głównych różnic między techniki alokacji dwóch jest, że za pomocą Alokacja ramek, zwykle działają z rzeczywistych pamięci zablokowanie, gdy za pomocą alokacji stosu, są zawsze podając wskaźnik do bloku pamięci. Inna główna różnica między dwa schematy jest, że obiekty ramki są automatycznie usuwane, gdy sterty obiektów, które muszą zostać jawnie usunięte przez programistę.  
  
 Dla innego typu niż MFC informacji na temat zarządzania pamięcią w programach dla Windows, zobacz [zarządzanie pamięcią](https://msdn.microsoft.com/library/windows/desktop/aa366779) w zestawie Windows SDK.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat  
  
-   [Alokacja ramek](../mfc/memory-management-frame-allocation.md)  
  
-   [Alokacja sterty](../mfc/memory-management-heap-allocation.md)  
  
-   [Przydzielanie pamięci dla tablic](../mfc/memory-management-examples.md)  
  
-   [Cofanie przydziału pamięci dla tablicy ze sterty](../mfc/memory-management-examples.md)  
  
-   [Przydzielanie pamięci dla struktury danych](../mfc/memory-management-examples.md)  
  
-   [Przydzielanie pamięci dla obiektu](../mfc/memory-management-examples.md)  
  
-   [Bloki pamięci o zmiennych rozmiarach](../mfc/memory-management-resizable-memory-blocks.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia](../mfc/mfc-concepts.md)   
 [Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)

