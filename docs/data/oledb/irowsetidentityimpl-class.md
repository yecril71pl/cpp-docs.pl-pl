---
title: Irowsetidentityimpl — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IRowsetIdentityImpl
- ATL.IRowsetIdentityImpl
- IRowsetIdentityImpl
- IsSameRow
- IRowsetIdentityImpl.IsSameRow
- ATL.IRowsetIdentityImpl.IsSameRow
- IRowsetIdentityImpl::IsSameRow
- ATL::IRowsetIdentityImpl::IsSameRow
dev_langs:
- C++
helpviewer_keywords:
- IRowsetIdentityImpl class
- IsSameRow method
ms.assetid: 56821edf-e045-40c8-96bd-231552cd5799
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1431fb9b35ab83f6cb0fc167eff4ba4508f2e301
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036192"
---
# <a name="irowsetidentityimpl-class"></a>IRowsetIdentityImpl — Klasa

Implementuje OLE DB [IRowsetIdentity](/previous-versions/windows/desktop/ms715913\(v=vs.85\)) interfejs, który umożliwia testowanie pod kątem tożsamość wiersza.  
  
## <a name="syntax"></a>Składnia

```cpp
template <class T, class RowClass = CSimpleRow>  
class ATL_NO_VTABLE IRowsetIdentityImpl   
   : public IRowsetIdentity  
```  
  
### <a name="parameters"></a>Parametry  

*T*<br/>
Klasa pochodząca z `IRowsetIdentityImpl`.  
  
*RowClass*<br/>
Jednostki magazynu na potrzeby `HROW`.  

## <a name="requirements"></a>Wymagania  

**Nagłówek:** atldb.h  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Issamerow —](#issamerow)|Porównuje dwa uchwytów wierszy, aby sprawdzić, czy odnoszą się do tego samego wiersza.|  
  
## <a name="issamerow"></a> IRowsetIdentityImpl::IsSameRow

Porównuje dwa uchwytów wierszy, aby sprawdzić, czy odnoszą się do tego samego wiersza.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
STDMETHOD(IsSameRow )(HROW hThisRow,  
   HROW hThatRow);  
```  
  
#### <a name="parameters"></a>Parametry  

Zobacz [IRowsetIdentity::IsSameRow](/previous-versions/windows/desktop/ms719629\(v=vs.85\)) w *OLE DB Podręcznik programisty*.  
  
### <a name="remarks"></a>Uwagi  

Aby porównać dojść do wierszy, ta metoda rzutuje `HROW` uchwytów na `RowClass` elementów członkowskich i wywołania `memcmp` na wskaźniki.  
  
## <a name="see-also"></a>Zobacz też  

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)