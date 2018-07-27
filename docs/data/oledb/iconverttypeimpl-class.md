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
ms.openlocfilehash: 0dfa073226dc4ddb3cd14b2aae31375a6f6ccc25
ms.sourcegitcommit: b0d6777cf4b580d093eaf6104d80a888706e7578
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2018
ms.locfileid: "39269786"
---
# <a name="iconverttypeimpl-class"></a>IConvertTypeImpl — Klasa
Udostępnia implementację [IConvertType](https://msdn.microsoft.com/library/ms715926.aspx) interfejsu.  
  
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
 Zobacz [IConvertType::CanConvert](https://msdn.microsoft.com/library/ms711224.aspx) w *OLE DB Podręcznik programisty*.  
  
### <a name="remarks"></a>Uwagi  
 Używa konwersji danych OLE DB w `MSADC.DLL`.  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
