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
ms.openlocfilehash: 84050dcf4faed8bb99b871d3b797400c1ed5620e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086957"
---
# <a name="iopenrowsetimpl-class"></a>IOpenRowsetImpl — Klasa

Udostępnia implementację dla `IOpenRowset` interfejsu.  
  
## <a name="syntax"></a>Składnia

```cpp
template <class SessionClass>  
class IOpenRowsetImpl : public IOpenRowset  
```  
  
### <a name="parameters"></a>Parametry  

*SessionClass*<br/>
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

[IOpenRowset](/previous-versions/windows/desktop/ms716946\(v=vs.85\)) interfejsu jest obowiązkowa, aby obiekt sesji. Otwiera i zwraca zestawu wierszy, który zawiera wszystkie wiersze z jednej tabeli bazowej lub indeksu.  
  
## <a name="createrowset"></a> IOpenRowsetImpl::CreateRowset

Tworzy obiekt zestawu wierszy. Nie jest wywoływana bezpośrednio przez użytkownika. Zobacz [IOpenRowset::OpenRowset](/previous-versions/windows/desktop/ms716724\(v=vs.85\)) w *OLE DB Podręcznik programisty.*  
  
### <a name="syntax"></a>Składnia  
  
```cpp
template template <class RowsetClass>  
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

*RowsetClass*<br/>
Składowa klasy szablonu reprezentująca klasy zestawów wierszy przez użytkownika. Zwykle generowane przez kreatora.  
  
*pRowsetObj*<br/>
[out] Wskaźnik do obiektu zestawu wierszy. Zazwyczaj ten parametr nie jest używany, ale mogą używane, jeśli konieczne jest przeprowadzenie więcej pracy na zestawie wierszy przed przekazaniem go do obiektu COM. Okres istnienia *pRowsetObj* jest ograniczone przez *ppRowset*.  
  
Dla innych parametrów, zobacz [IOpenRowset::OpenRowset](/previous-versions/windows/desktop/ms716724\(v=vs.85\)) w *OLE DB Podręcznik programisty.*  

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

Zobacz [IOpenRowset::OpenRowset](/previous-versions/windows/desktop/ms716724\(v=vs.85\)) w *OLE DB Podręcznik programisty*.  
  
### <a name="remarks"></a>Uwagi  

Ta metoda nie znajduje się w ATLDB. H. Jest on tworzony przez kreatora ATL obiektu po utworzeniu dostawcy usługi.  
  
## <a name="see-also"></a>Zobacz też  

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)