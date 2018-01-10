---
title: Paski dialogowe | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC, control bars
- CDialogBar class [MFC], dialog bars
- control bars [MFC], dialog bars
- dialog bars
- dialog bars [MFC], about dialog bars
ms.assetid: 485c8055-6bb0-4051-8417-dd2971499321
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3d9d7319f23741f683e31cfd683a8ebd6d25acdd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="dialog-bars"></a>Paski dialogowe
Paska dialogowego jest pasek narzędzi rodzaju z [pasek sterowania](../mfc/control-bars.md) które mogą zawierać dowolne formantu. Ponieważ ma on właściwości okno dialogowe niemodalne [cdialogbar —](../mfc/reference/cdialogbar-class.md) obiekt zapewnia bardziej zaawansowanych narzędzi.  
  
 Istnieje kilka podstawowych różnic między paska narzędzi i `CDialogBar` obiektu. A `CDialogBar` obiektu jest tworzona na podstawie szablonu okna dialogowego zasobu, można utworzyć z edytora okien dialogowych programu Visual C++ i które mogą zawierać dowolny rodzaj kontrolki systemu Windows. Użytkownik może karcie z formantu do formantu. I mogą określać styl wyrównanie Dopasuj paska dialogowego z dowolną część ramkę okna nadrzędnego, a nawet pozostawić go w miejscu, jeśli zmieni się rozmiar obiektu nadrzędnego. Na poniższej ilustracji przedstawiono paska dialogowego z szerokiej gamy kontrolek.  
  
 ![Pasek dialogowy programu VC](../mfc/media/vc378t1.gif "vc378t1")  
Paska dialogowego  
  
 Pod innymi względami, Praca z `CDialogBar` obiekt jest tak jak w przypadku niemodalne okno dialogowe. Edytor okien dialogowych umożliwia projektowanie i tworzenie zasobu okna dialogowego.  
  
 Jedną z zalet pasków okna dialogowego jest mogą zawierać formantów innych niż przycisków.  
  
 W trakcie normalnej pochodzić własne klasy okien dialogowych z `CDialog`, nie zwykle pochodzi klasy dla paska dialogowego. Paski dialogowe są takie jak rozszerzenia do głównego okna i komunikaty powiadomień dotyczących formantu paska dialogowego **BN_CLICKED** lub **EN_CHANGE**, zostaną wysłane do nadrzędnego okna dialogowego paska głównego okna.  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)   
 [Próbki](../visual-cpp-samples.md)

