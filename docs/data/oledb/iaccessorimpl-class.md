---
title: "Iaccessorimpl — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IAccessorImpl
dev_langs: C++
helpviewer_keywords: IAccessorImpl class
ms.assetid: 768606da-8b71-417c-a62c-88069ce7730d
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fb76054313946df5b085081a3a619ae3fb3de2ec
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="iaccessorimpl-class"></a>IAccessorImpl — Klasa
Udostępnia implementację elementu [IAccessor](https://msdn.microsoft.com/en-us/library/ms719672.aspx) interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <  
   class T,   
   class BindType = ATLBINDINGS,   
   class BindingVector = CAtlMap <   
      HACCESSOR hAccessor,   
      BindType* pBindingsStructure   
   >   
>  
class ATL_NO_VTABLE IAccessorImpl : public IAccessorImplBase<BindType>  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Klasy obiektu zestawu wierszy lub polecenie.  
  
 `BindType`  
 Jednostki magazynu, aby uzyskać informacje o wiązaniu. Wartość domyślna to **ATLBINDINGS** struktury (zobacz atldb.h).  
  
 `BindingVector`  
 Jednostki magazynu dla informacji o kolumnie. Wartość domyślna to [CAtlMap](../../atl/reference/catlmap-class.md) jeżeli jest kluczowy element **HACCESSOR** wartość i wartość elementu jest wskaźnikiem do `BindType` struktury.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Iaccessorimpl —](../../data/oledb/iaccessorimpl-class.md)|Konstruktor.|  
  
### <a name="interface-methods"></a>Metody interfejsu  
  
|||  
|-|-|  
|[AddRefAccessor](../../data/oledb/iaccessorimpl-addrefaccessor.md)|Dodaje liczba odwołań do istniejących metody dostępu.|  
|[CreateAccessor](../../data/oledb/iaccessorimpl-createaccessor.md)|Tworzy metody dostępu przy użyciu zestawu powiązań.|  
|[GetBindings](../../data/oledb/iaccessorimpl-getbindings.md)|Zwraca powiązania w metodzie dostępu.|  
|[ReleaseAccessor](../../data/oledb/iaccessorimpl-releaseaccessor.md)|Udostępnia metody dostępu.|  
  
## <a name="remarks"></a>Uwagi  
 Jest to obowiązkowa w przypadku poleceń i zestawy wierszy. OLE DB wymaga dostawców do zaimplementowania **HACCESSOR**, która jest tag do tablicy [DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) struktury. **HACCESSOR**s dostarczonych przez `IAccessorImpl` są adresy `BindType` struktury. Domyślnie `BindType` jest zdefiniowany jako **ATLBINDINGS** w `IAccessorImpl`w definicji szablonu. `BindType`udostępnia mechanizm używany przez `IAccessorImpl` można śledzić liczbę elementów w jego **DBBINDING** array, a także flagi metody dostępu i liczba odwołania.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)