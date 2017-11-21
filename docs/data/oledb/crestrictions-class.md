---
title: Klasa CRestrictions | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CRestrictions
- CRestrictions
- ATL.CRestrictions
dev_langs: C++
helpviewer_keywords: CRestrictions class
ms.assetid: 0aaa2364-641c-4318-b110-7446aada4b4f
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 88ba3c853bbd12c1512dbb8c70c0941718b1396f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="crestrictions-class"></a>Klasa CRestrictions
Ogólny klasy, która pozwala określić ograniczenia dotyczące zestawów wierszy schematu.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <   
   class T,   
   short nRestrictions,   
   const GUID* pguid   
>  
class CRestrictions : public CSchemaRowset <   
   T,   
   nRestrictions   
>  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Klasa używana do dostępu.  
  
 `nRestrictions`  
 Liczba kolumn ograniczeń dla zestawu wierszy schematu.  
  
 `pguid`  
 Wskaźnik do identyfikatora GUID schematu.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Otwórz](../../data/oledb/crestrictions-open.md)|Zwraca wynik ustawiony odpowiednio do atrybutów ograniczenia dostarczone przez użytkownika.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbsch.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Dokumentacja szablonów konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)