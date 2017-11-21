---
title: "Punkty połączenia ATL | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- connections, connection points
- ATL, connection points
- connection points [C++], about connection points
ms.assetid: 17d76165-5f83-4f95-b36d-483821c247a1
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e0ef927ad6e2a0e9b0c71e211fa525ba7fc8ea0d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="atl-connection-points"></a>Punkty połączenia ATL
Obiekt składnika jest taki, który obsługuje interfejsy wychodzących. Wychodzące interfejs sprawia, że obiekt do komunikacji z klientem. Dla każdego interfejsu wychodzącego składnika obiekt ujawnia punktu połączenia. Każdy wychodzących interfejs jest implementowany przez klienta do obiektu o nazwie zbiorniku.  
  
 ![Punkty połączenia](../atl/media/vc2zw31.gif "vc2zw31")  
  
 Każdy punkt połączenia obsługuje [IConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms694318) interfejsu. Obiekt składnika udostępnia jego punkty połączenia klienta za pośrednictwem [IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857) interfejsu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Klasy punktu połączenia ATL](../atl/atl-connection-point-classes.md)  
 Krótko opisano klasy ATL, które obsługują punkty połączenia.  
  
 [Dodawanie punktów połączenia do obiektu](../atl/adding-connection-points-to-an-object.md)  
 Omówiono kroki umożliwiają dodawanie punkty połączenia do obiektu.  
  
 [Przykład punktu połączenia ATL](../atl/atl-connection-point-example.md)  
 Przykład deklarowanie punktu połączenia.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 Zawiera łącza do tematów koncepcyjne na temat programowania przy użyciu biblioteki Active Template Library.  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia](../atl/active-template-library-atl-concepts.md)

