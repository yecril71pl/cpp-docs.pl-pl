---
title: Kreator implementacji punktu połączenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.impl.cp.overview
dev_langs:
- C++
helpviewer_keywords:
- Implement Connection Point Wizard [C++]
ms.assetid: c117f6c6-30f0-4adb-82b4-b1f34e0f0fa8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ef2f7efa92de3714170e403ea50b5f486c8367d6
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "33323761"
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