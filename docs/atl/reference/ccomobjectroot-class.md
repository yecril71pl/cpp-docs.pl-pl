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
ms.openlocfilehash: d2832b9866145d9af510302c8c6d327972205495
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38952971"
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
 [Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)   
 [Klasa CComAggObject](../../atl/reference/ccomaggobject-class.md)   
 [Klasa CComObject](../../atl/reference/ccomobject-class.md)   
 [Klasa CComPolyObject](../../atl/reference/ccompolyobject-class.md)   
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
