---
title: Interfejsy (ATL) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 95dce7d707cfb29c8f33f94504c26b5b24ef4c4f
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
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

