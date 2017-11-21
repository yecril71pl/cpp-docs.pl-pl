---
title: Wprowadzenie do COM | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: 'index-page '
dev_langs: C++
helpviewer_keywords: COM
ms.assetid: 120735d9-db71-4ad3-a730-ce576ea2354e
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 236222296b270fe52f43f42a823e3f6f790d08ca
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="introduction-to-com"></a>Wprowadzenie do COM
COM jest podstawowe "model obiektu", na które kontrolki ActiveX i OLE są tworzone. COM umożliwia obiektu do udostępnienia jej funkcji do innych składników i umożliwia obsługę aplikacji. Określa ona zarówno jak obiekt ujawnia się i działania tego narażenia na między procesami i sieci. COM definiuje również cyklu życia obiektu.  
  
 Podstawowe dla modelu COM są te pojęcia:  
  
-   [Interfejsy](../atl/interfaces-atl.md) — mechanizm, za pośrednictwem której obiekt ujawnia jej funkcji.  
  
-   [IUnknown](../atl/iunknown.md) — podstawowy interfejs pozostałe podstawie. Implementuje liczenie odwołań i interfejs podczas badania mechanizmów uruchomiony za pośrednictwem modelu COM.  
  
-   [Liczenie odwołań w](../atl/reference-counting.md) — metoda, za pomocą którego obiektu (lub ściśle, interfejs) decyduje o tym, kiedy jest już używany i w związku z tym będzie mógł się usunąć.  
  
-   [QueryInterface](../atl/queryinterface.md) — metoda wykorzystywane do badania obiektu dla danego interfejsu.  
  
-   [Organizowanie](../atl/marshaling.md) — mechanizm, który pozwala obiektów do użycia w wątku, procesów i granic sieci, co zapewnia niezależność od lokalizacji.  
  
-   [Agregacja](../atl/aggregation.md) — sposób, w którym można wprowadzić jeden obiekt użyć innego.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do COM i ATL](../atl/introduction-to-com-and-atl.md)   
 [Model Component Object Model](http://msdn.microsoft.com/library/windows/desktop/ms694363)

