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
ms.openlocfilehash: 92312bc130ed24f2aafe2e4b95e2c4bcf6381215
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429672"
---
# <a name="implement-connection-point-wizard"></a>Kreator implementacji punktu połączenia

Ten kreator implementuje punkt połączenia dla obiektów COM. Obiekt łączności (źródła) można uwidocznić punkt połączenia dla swoich własnych interfejsów lub dowolnego interfejsu wychodzącego. Visual C++ Windows zarówno i zapewniają bibliotek typów, które mają wychodzących interfejsów. Każdego interfejsu wychodzącego może być implementowana przez klienta do obiektu (ujścia).

Aby uzyskać więcej informacji, zobacz [punkty połączenia ATL](../atl/atl-connection-points.md).

- **Biblioteki typów dostępne**

   Wyświetla bibliotek dostępnych typów zawierający definicje interfejsu, dla których można wdrożyć punktów połączenia. Kliknij przycisk wielokropka, aby zlokalizować pliku zawierającego bibliotekę typów, aby użyć.

- **Lokalizacja**

   Wyświetla lokalizację biblioteki typów, aktualnie wybrane w **bibliotek typów dostępnych** listy.

- **Interfejsy**

   Wyświetla interfejsy, których definicje znajdują się w aktualnie wybranego w bibliotece typów **bibliotek typów dostępnych** pole.

   |Przycisk transferu|Opis|
   |---------------------|-----------------|
   |**>**|Dodaje do **zaimplementować punkty połączenia** Nazwa interfejsu, aktualnie wybrane w listy **interfejsów** listy.|
   |**>>**|Dodaje do **zaimplementować punkty połączenia** listy dostępny w wszystkich nazw interfejsu **interfejsów** listy.|
   |**\<**|Usuwa nazwę interfejsu aktualnie wybrany w **zaimplementować punkty połączenia** listy.|
   |**\<\<**|Usuwa wszystkie interfejsu nazwy obecnie wymienione w **zaimplementować punkty połączenia** listy.|

- **Implementowanie punkty połączenia**

   Wyświetla nazwy interfejsów, które można zaimplementować punkty połączenia po kliknięciu **Zakończ**.

## <a name="see-also"></a>Zobacz też

[Implementacja punktu połączenia](../ide/implementing-a-connection-point-visual-cpp.md)