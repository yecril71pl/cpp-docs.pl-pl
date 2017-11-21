---
title: "Kreator implementacji punktu połączenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.impl.cp.overview
dev_langs: C++
helpviewer_keywords: Implement Connection Point Wizard [C++]
ms.assetid: c117f6c6-30f0-4adb-82b4-b1f34e0f0fa8
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a7efade7f0bd0a3c35e02439818873b923c1ac1d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="implement-connection-point-wizard"></a>Kreator implementacji punktu połączenia
Ten kreator implementuje punkt połączenia dla obiekt COM. Obiekt składnika (źródło) mogą uwidaczniać punktu połączenia dla własnej interfejsów lub dla dowolnego interfejsu wychodzących. Visual C++ i system Windows zarówno zapewniają biblioteki typu, w których interfejsy wychodzących. Każdy interfejs wychodzącej może być zaimplementowany przez klienta do obiektu (zbiornika).  
  
 Aby uzyskać więcej informacji, zobacz [punkty połączenia ATL](../atl/atl-connection-points.md).  
  
 **Biblioteki typów dostępne**  
 Wyświetla dostępne type libraries zawierający definicje interfejsu, dla których można zaimplementować punkty połączenia. Kliknij przycisk wielokropka, aby zlokalizować plik zawierający typ bibliotekę do użycia.  
  
 **Lokalizacja**  
 Wyświetla lokalizację biblioteki typów aktualnie wybrane w **bibliotek typów dostępne** listy.  
  
 **Interfejsy**  
 Wyświetla interfejsy, w których definicje znajdują się w bibliotece typów aktualnie wybrane w **bibliotek typów dostępne** pole.  
  
|Przycisk transferu|Opis|  
|---------------------|-----------------|  
|**>**|Dodaje do **zaimplementować punkty połączenia** listy z nazwą interfejsu aktualnie wybrane w **interfejsów** listy.|  
|**>>**|Dodaje do **zaimplementować punkty połączenia** listę wszystkich nazw interfejsu dostępne w **interfejsów** listy.|  
|**<**|Usuwa nazwę interfejsu aktualnie wybrane w **zaimplementować punkty połączenia** listy.|  
|**<<**|Usuwa wszystkie interfejsu nazw znajdujących się na liście w **zaimplementować punkty połączenia** listy.|  
  
 **Implementowanie punkty połączenia**  
 Wyświetla nazwy interfejsów, które można zaimplementować punkty połączenia po kliknięciu **Zakończ**.  
  
## <a name="see-also"></a>Zobacz też  
 [Implementacja punktu połączenia](../ide/implementing-a-connection-point-visual-cpp.md)