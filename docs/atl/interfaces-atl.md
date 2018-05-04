---
title: Interfejsy (ATL) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0db5a79f187cb0fe320bf67aace751a5d4c537d3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="interfaces-atl"></a>Interfejsy (ALT)
Interfejs jest sposób, w którym obiekt ujawnia jego działanie na zewnątrz. W modelu COM interfejs jest tabeli wskaźników (na przykład C++ vtable) do funkcji implementowane przez obiekt. Tabeli reprezentuje interfejs i funkcje, które wskazuje to metody tego interfejsu. Obiekt mogą uwidaczniać tyle interfejsy jako wybiera.  
  
 Każdy interfejs jest oparty na interfejsie COM podstawowych [IUnknown](../atl/iunknown.md). Metody **IUnknown** Zezwalaj nawigacji do innych interfejsów uwidaczniane przez obiekt.  
  
 Ponadto każdy interfejs otrzymuje interfejsu Unikatowy identyfikator (IID). Ta unikatowości ułatwia obsługuje przechowywanie wersji interfejsu. Po prostu nowy interfejs, z nowego identyfikatora IID jest nowa wersja interfejsu.  
  
> [!NOTE]
>  IID dla standardowych interfejsów COM i OLE są wstępnie zdefiniowane.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do COM](../atl/introduction-to-com.md)   
 [Obiekty COM i interfejsy](http://msdn.microsoft.com/library/windows/desktop/ms690343)

