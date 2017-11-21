---
title: "Carrayrowset — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CArrayRowset<TAccessor>
- ATL.CArrayRowset
- CArrayRowset
- ATL::CArrayRowset
- ATL::CArrayRowset<TAccessor>
dev_langs: C++
helpviewer_keywords: CArrayRowset class
ms.assetid: 511427e1-73ca-4fd8-9ba1-ae9463557cb6
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 82c209938c7d124e787310cb859aeb6191f32c8d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="carrayrowset-class"></a>CArrayRowset — Klasa
Elementy uzyskuje dostęp do zestawu wierszy za pomocą składni tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```  
template < class TAccessor >  
class CArrayRowset :   
   public CVirtualBuffer <TAccessor>,   
   protected CBulkRowset <TAccessor>  
```  
  
#### <a name="parameters"></a>Parametry  
 `TAccessor`  
 Typ klasy akcesor ma wierszy do użycia.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Carrayrowset —](../../data/oledb/carrayrowset-carrayrowset.md)|Konstruktor.|  
|[Migawki](../../data/oledb/carrayrowset-snapshot.md)|Odczytuje całego zestawu wierszy do pamięci.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[Operator &#91; &#93;](../../data/oledb/carrayrowset-operator.md)|Uzyskuje dostęp do elementu zestawu wierszy.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|||  
|-|-|  
|[CArrayRowset::m_nRowsRead](../../data/oledb/carrayrowset-m-nrowsread.md)|Liczba wierszy już przeczytana.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Dokumentacja szablonów konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [Crowset — klasa](../../data/oledb/crowset-class.md)