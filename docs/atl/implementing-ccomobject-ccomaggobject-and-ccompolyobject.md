---
title: Implementowanie klas CComObject, CComAggObject i CComPolyObject
ms.date: 11/04/2016
helpviewer_keywords:
- CComPolyObject class, implementing
- CreateInstance method
- CComAggObject class
- CComObject class, implementing
ms.assetid: 5aabe938-104d-492e-9c41-9f7fb1c62098
ms.openlocfilehash: e2413c8fb9f5722f0245883c947067387838e57f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62261790"
---
# <a name="implementing-ccomobject-ccomaggobject-and-ccompolyobject"></a>Implementowanie klas CComObject, CComAggObject i CComPolyObject

Klasy szablonów [CComObject](../atl/reference/ccomobject-class.md), [CComAggObject](../atl/reference/ccomaggobject-class.md), i [CComPolyObject](../atl/reference/ccompolyobject-class.md) są zawsze najbardziej pochodnej klasy w łańcuchu dziedziczenia. Swoją odpowiedzialność, aby zapewnić obsługę wszystkich metod w `IUnknown`: `QueryInterface`, `AddRef`, i `Release`. Ponadto `CComAggObject` i `CComPolyObject` (jeśli jest używane w przypadku obiektów zagregowane) zapewnia liczenie odwołań w specjalnych i `QueryInterface` semantyki wymagane dla wewnętrznego nieznany.

Czy `CComObject`, `CComAggObject`, lub `CComPolyObject` jest używana jest zależna od Zadeklaruj jedną (lub brak) następujących makr:

|Macro|Efekt|
|-----------|------------|
|DECLARE_NOT_AGGREGATABLE|Zawsze używa `CComObject`.|
|DECLARE_AGGREGATABLE|Używa `CComAggObject` Jeśli obiekt jest zagregowany i `CComObject` Jeśli tak nie jest. `CComCoClass` zawiera to makro, dlatego jeśli żadna z DECLARE_ * _AGGREGATABLE makra są zadeklarowane w klasie, będzie to wartość domyślna.|
|DECLARE_ONLY_AGGREGATABLE|Zawsze używa `CComAggObject`. Zwraca błąd, jeśli obiekt nie jest agregowany.|
|DECLARE_POLY_AGGREGATABLE|ATL tworzy wystąpienie **CComPolyObject\<CYourClass >** podczas `IClassFactory::CreateInstance` jest wywoływana. Podczas tworzenia jest sprawdzany wartość zewnętrzne nieznany. Jeśli ma wartość NULL, `IUnknown` został zaimplementowany dla obiektu nieagregowane. Jeśli nieznany zewnętrzny nie ma wartość NULL, `IUnknown` został zaimplementowany dla obiektu zagregowanego.|

Zaletą korzystania z `CComAggObject` i `CComObject` jest to, że implementacja `IUnknown` została zoptymalizowana pod kątem rodzaj tworzonego obiektu. Na przykład obiekt nieagregowane musi jedynie licznika odwołań podczas obiektu zagregowanego musi licznik odwołań dla nieznanego wewnętrzny i wskaźnik do zewnętrznego nieznany.

Zaletą korzystania z `CComPolyObject` to uniknąć konieczności zarówno `CComAggObject` i `CComObject` w module sposób obsługiwać przypadki zagregowane i nieagregowane. Pojedynczy `CComPolyObject` obiektu obsługuje w obu przypadkach. Oznacza to, że tylko jedna kopia vtable i jedną kopię funkcje istnieją w module. Jeśli Twoje vtable jest duży, to znacznie zmniejszyć rozmiar modułu. Jednak jeśli Twoja vtable jest mały, za pomocą `CComPolyObject` może spowodować nieco większy rozmiar modułu, ponieważ nie jest zoptymalizowana do zagregowanych lub nieagregowane obiektu, ponieważ są `CComAggObject` i `CComObject`.

## <a name="see-also"></a>Zobacz także

[Podstawowe informacje na temat obiektów COM ATL](../atl/fundamentals-of-atl-com-objects.md)<br/>
[Makra agregacji i fabryki klas](../atl/reference/aggregation-and-class-factory-macros.md)
