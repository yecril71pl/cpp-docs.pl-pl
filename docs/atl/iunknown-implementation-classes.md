---
title: Klasy implementacji interfejsu IUnknown (ATL) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- vc.atl.Iunknown
dev_langs:
- C++
helpviewer_keywords:
- IUnknown implementation classes
ms.assetid: 47b69bb5-69d8-4a9c-84a8-329bdde2bb3f
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 53d5363f6b11904e31ea0e9c6f452b2c8fa7e000
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="iunknown-implementation-classes"></a>Klasy implementacji interfejsu IUnknown
Następujące klasy wdrożenie **IUnknown** i powiązanych metod:  
  
-   [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) zarządza zliczanie zarówno zagregowane i nieagregowane obiektów. Umożliwia określanie modelu wątkowości.  
  
-   [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) zarządza zliczanie zarówno zagregowane i nieagregowane obiektów. Używa domyślnej model serwera wątków.  
  
-   [CComAggObject](../atl/reference/ccomaggobject-class.md) implementuje **IUnknown** dla obiekt zagregowanych.  
  
-   [Element CComObject](../atl/reference/ccomobject-class.md) implementuje **IUnknown** dla obiekt nieagregowane.  
  
-   [CComPolyObject](../atl/reference/ccompolyobject-class.md) implementuje **IUnknown** zagregowane i nieagregowane obiektów. Przy użyciu `CComPolyObject` pozwala uniknąć konieczności zarówno `CComAggObject` i `CComObject` w module. Pojedynczy `CComPolyObject` obiektu obsługuje zarówno zagregowane i nieagregowane przypadkach.  
  
-   [CComObjectNoLock](../atl/reference/ccomobjectnolock-class.md) implementuje **IUnknown** dla obiekt nieagregowane, bez konieczności modyfikacji liczbę blokad modułu.  
  
-   [CComTearOffObject](../atl/reference/ccomtearoffobject-class.md) implementuje **IUnknown** oderwania interfejsu.  
  
-   [CComCachedTearOffObject](../atl/reference/ccomcachedtearoffobject-class.md) implementuje **IUnknown** "pamięci podręcznej" interfejsu oderwania.  
  
-   [CComContainedObject](../atl/reference/ccomcontainedobject-class.md) implementuje **IUnknown** dla obiekt wewnętrzny agregacji lub oderwania interfejsu.  
  
-   [CComObjectGlobal](../atl/reference/ccomobjectglobal-class.md) służy do zarządzania nie będzie można usunąć liczebności referencyjnej w module zapewnienie obiektu.  
  
-   [CComObjectStack](../atl/reference/ccomobjectstack-class.md) tworzy tymczasowy obiekt COM za pomocą szkieletowych implementacja **IUnknown**.  
  
## <a name="related-articles"></a>Powiązane artykuły  
 [Podstawowe informacje na temat obiektów COM ATL](../atl/fundamentals-of-atl-com-objects.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../atl/atl-class-overview.md)   
 [Agregacja i makra fabryki klas](../atl/reference/aggregation-and-class-factory-macros.md)   
 [Makra mapy COM](../atl/reference/com-map-macros.md)   
 [Funkcje globalne mapy interfejsu COM](../atl/reference/com-map-global-functions.md)

