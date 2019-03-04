---
title: CComObjectRoot Class
ms.date: 11/04/2016
f1_keywords:
- CComObjectRoot
- atlcom/ATL::CComObjectRoot
helpviewer_keywords:
- CComObjectRoot class
ms.assetid: f8797c38-6e73-4f67-85c2-71654cffa8eb
ms.openlocfilehash: 9a9ffa1813fb15297d209894050b6bcce6802df2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57298649"
---
# <a name="ccomobjectroot-class"></a>CComObjectRoot Class

Ten element typedef dla [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) jest szablonowana na domyślny model serwera wątków.

## <a name="syntax"></a>Składnia

```
typedef CComObjectRootEx<CComObjectThreadModel> CComObjectRoot;
```

## <a name="remarks"></a>Uwagi

`CComObjectRoot` jest `typedef` z [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) szablonowana na domyślny model serwera wątków. Ten sposób [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) będzie odwoływać się albo [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) lub [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md).

`CComObjectRootEx` obsługuje zarządzanie liczba odwołanie do obiektu nieagregowane i zagregowane obiekty. Jeśli obiekt nie są agregowane i przechowuje wskaźnik nieznany zewnętrznego, jeśli obiekt są agregowane, przechowuje licznik odwołań obiektu. Zagregowane obiekty `CComObjectRootEx` metody może służyć do obsługi błędu wewnętrznego obiektu do utworzenia i ma być chroniony obiektu zewnętrznego przed usunięciem zwolnionych interfejsów wewnętrznych lub wewnętrzny obiekt zostanie usunięty.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="see-also"></a>Zobacz także

[Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[Klasa CComAggObject](../../atl/reference/ccomaggobject-class.md)<br/>
[Klasa CComObject](../../atl/reference/ccomobject-class.md)<br/>
[Klasa CComPolyObject](../../atl/reference/ccompolyobject-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
