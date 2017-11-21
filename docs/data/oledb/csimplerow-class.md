---
title: "Csimplerow — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CSimpleRow
- ATL::CSimpleRow
- ATL.CSimpleRow
dev_langs: C++
helpviewer_keywords: CSimpleRow class
ms.assetid: 06d9621d-60cc-4508-8b0c-528d1b1a809b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f8c7f1ca1823970dec3f9a8c1ceb0198bc8a71b2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="csimplerow-class"></a>CSimpleRow — Klasa
Udostępnia domyślną implementację dla dojście do wiersza, który jest używany w [irowsetimpl —](../../data/oledb/irowsetimpl-class.md) klasy.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CSimpleRow  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[AddRefRow](../../data/oledb/csimplerow-addrefrow.md)|Dodaje liczba odwołań do istniejących uchwyt wiersza.|  
|[Porównaj](../../data/oledb/csimplerow-compare.md)|Porównuje dwa wiersze, aby zobaczyć, czy odnoszą się do tego samego wystąpienia wiersza.|  
|[Csimplerow —](../../data/oledb/csimplerow-csimplerow.md)|Konstruktor.|  
|[ReleaseRow](../../data/oledb/csimplerow-releaserow.md)|Wersje wierszy.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|||  
|-|-|  
|[m_dwRef](../../data/oledb/csimplerow-m-dwref.md)|Liczba odwołań do istniejących uchwyt wiersza.|  
|[m_iRowset](../../data/oledb/csimplerow-m-irowset.md)|Indeks wierszy reprezentujący kursora.|  
  
## <a name="remarks"></a>Uwagi  
 Dojście do wiersza jest logicznie unikatowy tag dla wiersza wynik. `IRowsetImpl`Tworzy nowy `CSimpleRow` dla każdego wiersza w wymagane [IRowsetImpl::GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md). `CSimpleRow`również można zastąpić implementacji z dojściem do wiersza, ponieważ jest on domyślnym argumentem szablonu do `IRowsetImpl`. Jedynym wymaganiem zastąpienia tej klasy jest Klasa zastępcza, podaj konstruktora, który przyjmuje jeden parametr typu **DŁUGI**.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Irowsetimpl — klasa](../../data/oledb/irowsetimpl-class.md)