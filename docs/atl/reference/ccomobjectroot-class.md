---
title: Klasa klasy CComObjectRoot
ms.date: 11/04/2016
f1_keywords:
- CComObjectRoot
- atlcom/ATL::CComObjectRoot
helpviewer_keywords:
- CComObjectRoot class
ms.assetid: f8797c38-6e73-4f67-85c2-71654cffa8eb
ms.openlocfilehash: 98868e67fd14899a75f86837034ba540d22039e3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224243"
---
# <a name="ccomobjectroot-class"></a>Klasa klasy CComObjectRoot

Ten element typedef elementu [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) jest szablonowana na domyślnym modelu wątkowego serwera.

## <a name="syntax"></a>Składnia

```
typedef CComObjectRootEx<CComObjectThreadModel> CComObjectRoot;
```

## <a name="remarks"></a>Uwagi

`CComObjectRoot`jest elementem **`typedef`** [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) szablonowana na domyślnym modelu wątkowego serwera. W tym celu [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) odwołuje się do [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) lub [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md).

`CComObjectRootEx`obsługuje zarządzanie liczbami odwołań do obiektów zarówno dla obiektów niezagregowanych, jak i agregowanych. Zawiera licznik odwołań do obiektów, jeśli obiekt nie jest agregowany i utrzymuje wskaźnik do nieznanego obiektu zewnętrznego, jeśli obiekt jest agregowany. W przypadku obiektów agregowanych `CComObjectRootEx` metody mogą służyć do obsługi niepowodzenia obiektu wewnętrznego do skonstruowania oraz do ochrony zewnętrznego obiektu przed usunięciem po wydaniu interfejsów wewnętrznych lub usunięciu obiektu wewnętrznego.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

## <a name="see-also"></a>Zobacz także

[Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[Klasa CComAggObject](../../atl/reference/ccomaggobject-class.md)<br/>
[Klasa CComObject](../../atl/reference/ccomobject-class.md)<br/>
[Klasa CComPolyObject](../../atl/reference/ccompolyobject-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
