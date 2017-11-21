---
title: "Isessionpropertiesimpl — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ISessionPropertiesImpl
dev_langs: C++
helpviewer_keywords: ISessionPropertiesImpl class
ms.assetid: ca0ba254-c7dc-4c52-abec-cf895a0c6a63
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f8824ac2081ffd214402a23c6a5975e027ecf9ae
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="isessionpropertiesimpl-class"></a>ISessionPropertiesImpl — Klasa
Udostępnia implementację elementu [ISessionProperties](https://msdn.microsoft.com/en-us/library/ms713721.aspx) interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class T, class PropClass = T>  
class ATL_NO_VTABLE ISessionPropertiesImpl :  
   public ISessionProperties,    
   public CUtlProps<PropClass>  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `ISessionPropertiesImpl`.  
  
 `PropClass`  
 Klasa właściwości definiowane przez użytkownika, która domyślnie `T`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="interface-methods"></a>Metody interfejsu  
  
|||  
|-|-|  
|[GetProperties](../../data/oledb/isessionpropertiesimpl-getproperties.md)|Zwraca listę właściwości grupy właściwości sesji, które są aktualnie ustawione w tej sesji.|  
|[SetProperties](../../data/oledb/isessionpropertiesimpl-setproperties.md)|Ustawia właściwości w grupie właściwości sesji.|  
  
## <a name="remarks"></a>Uwagi  
 Obowiązkowego interfejsu na sesji. Ta klasa implementuje właściwości sesji przez wywołanie metody statycznej funkcji zdefiniowanej przez [mapę zestaw właściwości](../../data/oledb/begin-propset-map.md). Mapa zestaw właściwości powinny być określone w klasie sesji.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)