---
title: Klasa CTable | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CTable
- ATL.CTable
- CTable
- ATL.CTable.Open
- ATL::CTable::Open
- CTable::Open
- CTable.Open
dev_langs:
- C++
helpviewer_keywords:
- CTable class
- Open method
ms.assetid: f13fdaa3-e198-4557-977d-54b0bbc3454d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 723d4f1e8f44c3ce376b4f39f34a191265ca4eab
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2018
ms.locfileid: "39336729"
---
# <a name="ctable-class"></a>Klasa CTable
Zapewnia to uzyskać bezpośredni dostęp do prostego zestawu wierszy (bez parametrów).  
  
## <a name="syntax"></a>Składnia

```cpp
template <class TAccessor = CNoAccessor, 
            template <typename T> class TRowset = CRowset>  
class CTable :  
   public CAccessorRowset <TAccessor, TRowset>  
```  
  
### <a name="parameters"></a>Parametry  
 *TAccessor*  
 Klasa metody dostępu.  
  
 *TRowset*  
 Klasy zestawów wierszy.  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Otwórz](#open)|Zostanie otwarty tabeli.|  
  
## <a name="remarks"></a>Uwagi  
 Zobacz [CCommand](../../data/oledb/ccommand-class.md) informacji na temat sposobu wykonania polecenia do dostępu do zestawu wierszy.  

## <a name="open"></a> CTable::Open
Zostanie otwarty tabeli.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Open(const CSession& session,  
   LPCWSTR wszTableName,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0) throw ();  

HRESULT Open(const CSession& session,  
   LPCSTR szTableName,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0) throw ();  

HRESULT Open(const CSession& session,  
   DBID& dbid,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0) throw ();  
```  
  
#### <a name="parameters"></a>Parametry  
 *Sesji*  
 [in] Sesja otwieraniu tabeli.  
  
 *wszTableName*  
 [in] Nazwa tabeli, aby otworzyć, jest przekazywany jako ciąg Unicode.  
  
 *szTableName*  
 [in] Nazwa tabeli, aby otworzyć, jest przekazywany jako ciąg ANSI.  
  
 *dbid*  
 [in] `DBID` Tabeli, aby otworzyć.  
  
 *pPropSet*  
 [in] Wskaźnik do tablicy [DBPROPSET](https://msdn.microsoft.com/library/ms714367.aspx) struktury zawierający właściwości i wartości do ustawienia. Zobacz [zestawy właściwości i właściwości grupy](https://msdn.microsoft.com/library/ms713696.aspx) w *OLE DB Podręcznik programisty* w Windows SDK. Domyślna wartość NULL określa Brak właściwości.  
  
 *ulPropSets*  
 [in] Liczba [DBPROPSET](https://msdn.microsoft.com/library/ms714367.aspx) struktury przekazany *pPropSet* argumentu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [IOpenRowset::OpenRowset](https://msdn.microsoft.com/library/ms716724.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)   