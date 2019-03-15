---
title: Klasy implementacji interfejsu IUnknown (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IUnknown implementation classes
ms.assetid: 47b69bb5-69d8-4a9c-84a8-329bdde2bb3f
ms.openlocfilehash: 26751c013d65142393377394006a9833e6c8f7bb
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57814075"
---
# <a name="iunknown-implementation-classes"></a>Klasy implementacji interfejsu IUnknown

Następujące klasy implementacji `IUnknown` i powiązanych metod:

- [Klasy CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) zarządza zliczanie zagregowane i nieagregowane obiektów. Zezwala na określanie modelu wątkowości.

- [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) zarządza zliczanie zagregowane i nieagregowane obiektów. Korzysta z domyślnego modelu serwera wątków.

- [CComAggObject](../atl/reference/ccomaggobject-class.md) implementuje `IUnknown` dla obiektu zagregowanego.

- [CComObject](../atl/reference/ccomobject-class.md) implementuje `IUnknown` nieagregowane obiektu.

- [CComPolyObject](../atl/reference/ccompolyobject-class.md) implementuje `IUnknown` zagregowane i nieagregowane obiektów. Za pomocą `CComPolyObject` pozwala uniknąć konieczności zarówno `CComAggObject` i `CComObject` w module. Pojedynczy `CComPolyObject` obiektu obsługuje zarówno zagregowane i nieagregowane przypadkach.

- [CComObjectNoLock](../atl/reference/ccomobjectnolock-class.md) implementuje `IUnknown` nieagregowane obiektu, bez konieczności modyfikacji liczbę blokad modułu.

- [CComTearOffObject](../atl/reference/ccomtearoffobject-class.md) implementuje `IUnknown` odrywania interfejsu.

- [CComCachedTearOffObject](../atl/reference/ccomcachedtearoffobject-class.md) implementuje `IUnknown` "buforowane" interfejsu odrywania.

- [CComContainedObject](../atl/reference/ccomcontainedobject-class.md) implementuje `IUnknown` dla wewnętrznego obiektu agregacji lub interfejs odrywania.

- [CComObjectGlobal](../atl/reference/ccomobjectglobal-class.md) zarządza licznik odwołań do modułu, aby upewnić się, obiekt nie zostanie usunięty.

- [CComObjectStack](../atl/reference/ccomobjectstack-class.md) tworzy tymczasowy obiekt COM za pomocą implementacji szkieletowych `IUnknown`.

## <a name="related-articles"></a>Powiązane artykuły

[Podstawowe informacje na temat obiektów COM ATL](../atl/fundamentals-of-atl-com-objects.md)

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../atl/atl-class-overview.md)<br/>
[Makra agregacji i fabryki klas](../atl/reference/aggregation-and-class-factory-macros.md)<br/>
[Makra mapy modelu COM](../atl/reference/com-map-macros.md)<br/>
[Funkcje globalne mapy interfejsu COM](../atl/reference/com-map-global-functions.md)
