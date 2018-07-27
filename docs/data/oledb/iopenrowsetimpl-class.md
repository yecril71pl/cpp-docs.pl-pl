---
title: Iopenrowsetimpl — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IOpenRowsetImpl
- IOpenRowsetImpl.CreateRowset
- IOpenRowsetImpl::CreateRowset
- CreateRowset
- OpenRowset
- IOpenRowsetImpl::OpenRowset
- IOpenRowsetImpl.OpenRowset
dev_langs:
- C++
helpviewer_keywords:
- IOpenRowsetImpl class
- CreateRowset method
- OpenRowset method
ms.assetid: d259cedc-1db4-41cf-bc9f-5030907ab486
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dd3281aa21cfd20caa902572e9ad39e16a18e6f6
ms.sourcegitcommit: b0d6777cf4b580d093eaf6104d80a888706e7578
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2018
ms.locfileid: "39269829"
---
# <a name="iopenrowsetimpl-class"></a>IOpenRowsetImpl — Klasa
Udostępnia implementację dla `IOpenRowset` interfejsu.  
  
## <a name="syntax"></a>Składnia

```cpp
template <class SessionClass>  
class IOpenRowsetImpl : public IOpenRowset  
```  
  
### <a name="parameters"></a>Parametry  
 *SessionClass*  
 Z klasą pochodną `IOpenRowsetImpl`.  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Createrowset —](#createrowset)|Tworzy obiekt zestawu wierszy. Nie jest wywoływana bezpośrednio przez użytkownika.|  
|[OpenRowset](#openrowset)|Zostanie otwarty i zwraca zestawu wierszy, który zawiera wszystkie wiersze z jednej tabeli bazowej lub indeksu. (Nie w ATLDB. GODZ.)|  
  
## <a name="remarks"></a>Uwagi  
 [IOpenRowset](https://msdn.microsoft.com/library/ms716946.aspx) interfejsu jest obowiązkowa, aby obiekt sesji. Otwiera i zwraca zestawu wierszy, który zawiera wszystkie wiersze z jednej tabeli bazowej lub indeksu.  
  
## <a name="createrowset"></a> IOpenRowsetImpl::CreateRowset
Tworzy obiekt zestawu wierszy. Nie jest wywoływana bezpośrednio przez użytkownika. Zobacz [IOpenRowset::OpenRowset](https://msdn.microsoft.com/library/ms716724.aspx) w *OLE DB Podręcznik programisty.*  
  
### <a name="syntax"></a>Składnia  
  
```cpp
      template template <class RowsetClass  
      >  
HRESULT CreateRowset(IUnknown* pUnkOuter,  
   DBID* pTableID,  
   DBID* pIndexID,  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown** ppRowset,  
   RowsetClass*& pRowsetObj);  
```  
  
#### <a name="parameters"></a>Parametry  
 *RowsetClass*  
 Składowa klasy szablonu reprezentująca klasy zestawów wierszy przez użytkownika. Zwykle generowane przez kreatora.  
  
 *pRowsetObj*  
 [out] Wskaźnik do obiektu zestawu wierszy. Zazwyczaj ten parametr nie jest używany, ale mogą używane, jeśli konieczne jest przeprowadzenie więcej pracy na zestawie wierszy przed przekazaniem go do obiektu COM. Okres istnienia *pRowsetObj* jest ograniczone przez *ppRowset*.  
  
 Dla innych parametrów, zobacz [IOpenRowset::OpenRowset](https://msdn.microsoft.com/library/ms716724.aspx) w *OLE DB Podręcznik programisty.*  

## <a name="openrowset"></a> IOpenRowsetImpl::OpenRowset
Zostanie otwarty i zwraca zestawu wierszy, który zawiera wszystkie wiersze z jednej tabeli bazowej lub indeksu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OpenRowset(IUnknown* pUnkOuter,  
   DBID* pTableID,  
   DBID* pIndexID,  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown** ppRowset);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IOpenRowset::OpenRowset](https://msdn.microsoft.com/library/ms716724.aspx) w *OLE DB Podręcznik programisty*.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda nie znajduje się w ATLDB. H. Jest on tworzony przez kreatora ATL obiektu po utworzeniu dostawcy usługi.  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
