---
title: Wprowadzenie do COM | Dokumentacja firmy Microsoft
ms.custom: index-page
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- COM
ms.assetid: 120735d9-db71-4ad3-a730-ce576ea2354e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 938d0c45cae5ec9a2988f77f539af1a3d5513b83
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356178"
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

