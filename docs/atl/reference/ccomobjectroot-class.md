---
title: Klasa CComObjectRoot | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComObjectRoot
- atlcom/ATL::CComObjectRoot
dev_langs:
- C++
helpviewer_keywords:
- CComObjectRoot class
ms.assetid: f8797c38-6e73-4f67-85c2-71654cffa8eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2647ea3ac46ec3783f584de996c3d988c168980d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054866"
---
# <a name="ccomobjectroot-class"></a>Klasa CComObjectRoot

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

## <a name="see-also"></a>Zobacz też

[Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[Klasa CComAggObject](../../atl/reference/ccomaggobject-class.md)<br/>
[Klasa CComObject](../../atl/reference/ccomobject-class.md)<br/>
[Klasa CComPolyObject](../../atl/reference/ccompolyobject-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
