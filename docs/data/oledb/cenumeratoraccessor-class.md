---
title: "Cenumeratoraccessor — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CEnumeratorAccessor
- CEnumeratorAccessor
- ATL.CEnumeratorAccessor
dev_langs: C++
helpviewer_keywords: CEnumeratorAccessor class
ms.assetid: 21e8e7ea-3511-4afe-b33f-d520f4ff82bb
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b78307c1b8f9df1945ab2376b939db2c41b8ad23
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cenumeratoraccessor-class"></a>CEnumeratorAccessor — Klasa
Używane przez [CEnumerator](../../data/oledb/cenumerator-class.md) dostępu do danych z zestawu wierszy modułu wyliczającego.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CEnumeratorAccessor  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|||  
|-|-|  
|[m_bIsParent](../../data/oledb/cenumeratoraccessor-m-bisparent.md)|Zmienna wskazującą, czy moduł wyliczający jest wyliczający nadrzędnego, jeśli wiersz jest moduł wyliczający.|  
|[m_nType](../../data/oledb/cenumeratoraccessor-m-ntype.md)|Zmienna wskazującą, czy wiersz zawiera opis źródła danych lub moduł wyliczający.|  
|[m_szDescription](../../data/oledb/cenumeratoraccessor-m-szdescription.md)|Opis źródła danych lub modułu wyliczającego.|  
|[m_szName](../../data/oledb/cenumeratoraccessor-m-szname.md)|Nazwa źródła danych lub modułu wyliczającego.|  
|[m_szParseName](../../data/oledb/cenumeratoraccessor-m-szparsename.md)|Parametry do przekazania do [IParseDisplayName](http://msdn.microsoft.com/library/windows/desktop/ms680604) uzyskanie moniker dla źródła danych lub modułu wyliczającego.|  
  
## <a name="remarks"></a>Uwagi  
 Ten zestaw wierszy składa się z źródła danych i moduły wyliczające widoczne z bieżącej modułu wyliczającego.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Dokumentacja szablonów konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)