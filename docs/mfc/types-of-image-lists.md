---
title: "Typy list obrazów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- lists [MFC], image
- image lists [MFC], types of
- CImageList class [MFC], types
ms.assetid: bee5e7c3-78f5-4037-a136-9c50d67cdee5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 84a2118978d5ebd722d4fe56cdeec2aa0f74a94e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="types-of-image-lists"></a>Typy list obrazów
Istnieją dwa typy list obrazów ([CImageList](../mfc/reference/cimagelist-class.md)): nonmasked i maskowanego. "Listy obrazów nonmasked" składa się z mapy bitowej kolor, który zawiera jeden lub więcej obrazów. "Listy obrazów maskowanego" składa się z dwóch map bitowych taki sam rozmiar. Pierwsza to kolorów mapy bitowej, zawierający obrazy, a drugą jest monochromatyczny mapy bitowej, który zawiera szereg maski — po jednej dla każdego obrazu w pierwszym mapy bitowej.  
  
 Jeden z przeciążeń **Utwórz** funkcji członkowskiej pobiera flagę wskazującą, czy listy obrazów są wyświetlane jako znaki. (Inne przeciążenia tworzenie list obrazów maskowanego).  
  
 Podczas rysowania obrazu nonmasked po prostu jest kopiowany do kontekstu urządzenia docelowego; oznacza to, że jest rysowane przez istniejący kolor tła kontekst urządzenia. Podczas rysowania obrazu maskowanego bitów obrazu są łączone z bity maski, zazwyczaj tworzenie obszarów przezroczystych w mapie bitowej którym wyświetlana kolor tła kontekstu urządzenia docelowego za pośrednictwem. Można określić kilka Style rysowania podczas rysowania obrazu maskowanego. Na przykład można określić, czy obraz ma być symulowane wskazująca wybranego obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CImageList](../mfc/using-cimagelist.md)   
 [Kontrolki](../mfc/controls-mfc.md)

