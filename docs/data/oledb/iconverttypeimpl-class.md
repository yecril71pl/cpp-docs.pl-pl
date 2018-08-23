---
title: Iconverttypeimpl — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IConvertTypeImpl<T>
- IConvertTypeImpl
- ATL.IConvertTypeImpl
- ATL::IConvertTypeImpl
- ATL::IConvertTypeImpl<T>
- IConvertTypeImpl.CanConvert
- CanConvert
- IConvertTypeImpl::CanConvert
dev_langs:
- C++
helpviewer_keywords:
- IConvertTypeImpl class
- CanConvert method
ms.assetid: 7f81e79e-7d3f-4cbe-b93c-d632a94b15f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e176cc20dc3f6f13eb868133b99c0ce7e86d25c4
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42464487"
---
# <a name="iconverttypeimpl-class"></a>IConvertTypeImpl — Klasa
Udostępnia implementację [IConvertType](/previous-versions/windows/desktop/ms715926\(v=vs.85\)) interfejsu.  
  
## <a name="syntax"></a>Składnia

```cpp
template <class T>  
class ATL_NO_VTABLE IConvertTypeImpl   
   : public IConvertType, public CConvertHelper  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Z klasą pochodną `IConvertTypeImpl`.  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="interface-methods"></a>Metody interfejsu  
  
|||  
|-|-|  
|[CanConvert](#canconvert)|Udostępnia informacje o dostępności konwersje typów dotyczącą polecenia lub w zestawie wierszy.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest obowiązkowa w przypadku poleceń, zestawy wierszy i zestawy wierszy indeksu. `IConvertTypeImpl` implementuje interfejs przez delegowanie do konwersji obiektu pochodzącego z OLE DB.  

## <a name="canconvert"></a> IConvertTypeImpl::CanConvert
Udostępnia informacje o dostępności konwersje typów dotyczącą polecenia lub w zestawie wierszy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
STDMETHOD(CanConvert)(DBTYPE wFromType,   
   DBTYPE wToType,   
   DBCONVERTFLAGS dwConvertFlags);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IConvertType::CanConvert](/previous-versions/windows/desktop/ms711224\(v=vs.85\)) w *OLE DB Podręcznik programisty*.  
  
### <a name="remarks"></a>Uwagi  
 Używa konwersji danych OLE DB w `MSADC.DLL`.  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)