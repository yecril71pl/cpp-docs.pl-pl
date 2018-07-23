---
title: Caccessorrowset — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CAccessorRowset
- ATL.CAccessorRowset
- ATL::CAccessorRowset
- CAccessorRowset.Bind
- CAccessorRowset::Bind
- CAccessorRowset::CAccessorRowset
- CAccessorRowset.CAccessorRowset
- CAccessorRowset
- ATL.CAccessorRowset.CAccessorRowset
- ATL::CAccessorRowset::CAccessorRowset
- CAccessorRowset.Close
- CAccessorRowset::Close
- CAccessorRowset::FreeRecordMemory
- CAccessorRowset.FreeRecordMemory
- FreeRecordMemory
- GetColumnInfo
- CAccessorRowset.GetColumnInfo
- CAccessorRowset::GetColumnInfo
dev_langs:
- C++
helpviewer_keywords:
- CAccessorRowset class
- CAccessorRowset class, methods
- CAccessorRowset class, members
- Bind method
- CAccessorRowset class, constructor
- Close method
- FreeRecordMemory method
- GetColumnInfo method
ms.assetid: bd4f58ed-cebf-4d43-8985-1e5fcbf06953
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a9f869a901885b064ef4ddbbfddc23b246455a39
ms.sourcegitcommit: 04d327940787df1297b72d534f388a035d472af0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2018
ms.locfileid: "39181188"
---
# <a name="caccessorrowset-class"></a>CAccessorRowset — Klasa
Hermetyzuje zestawu wierszy i skojarzone metody dostępu w jednej klasie.  
  
## <a name="syntax"></a>Składnia

```cpp
template <class TAccessor = CNoAccessor, 
          template <typename T> class TRowset = CRowset>  
class CAccessorRowset : public TAccessor, public TRowset<TAccessor>  
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
|[powiązania](#bind)|Tworzy powiązania (używane podczas `bBind` jest określony jako **false** w [CCommand::Open](../../data/oledb/ccommand-open.md)).|  
|[CAccessorRowset](#caccessorrowset)|Konstruktor.|  
|[Zamknij](#close)|Zamyka zestawu wierszy i wszelkie metody dostępu.|  
|[FreeRecordMemory](#freerecordmemory)|Zwalnia wszystkie kolumny w bieżącym rekordzie, które muszą zostać uwolniona.|  
|[GetColumnInfo](#getcolumninfo)|Implementuje [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx).|  
  
## <a name="remarks"></a>Uwagi  
 Klasa `TAccessor` zarządza akcesor. Klasa *TRowset* zarządza zestawu wierszy.  

## <a name="bind"></a> CAccessorRowset::Bind
Tworzy powiązania, jeśli określono `bBind` jako **false** w [CCommand::Open](../../data/oledb/ccommand-open.md).  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Bind();  
  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa HRESULT.  

## <a name="caccessorrowset"></a> CAccessorRowset::CAccessorRowset
Inicjuje `CAccessorRowset` obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
CAccessorRowset();  
  
```  

## <a name="close"></a> CAccessorRowset::Close
Zwalnia wszelkie aktywne metody dostępu i zestawu wierszy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
void Close();  
  
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie skojarzone pamięci.  

## <a name="freerecordmemory"></a> CAccessorRowset::FreeRecordMemory
Zwalnia wszystkie kolumny w bieżącym rekordzie, które muszą zostać uwolniona.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
void FreeRecordMemory();  
  
```  

## <a name="getcolumninfo"></a> CAccessorRowset::GetColumnInfo
Pobiera informacje o kolumnach z otwartego zestawu wierszy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetColumnInfo(DBORDINAL* pulColumns,  
   DBCOLUMNINFO** ppColumnInfo,  
   LPOLESTR* ppStrings) const;  

HRESULT GetColumnInfo(DBORDINAL* pColumns,  
   DBCOLUMNINFO** ppColumnInfo);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx) w *OLE DB Podręcznik programisty*.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Użytkownik należy zwolnić informacji zwróconej kolumny i buforu ciągu. Użyj drugą wersję tej metody, gdy używasz [cdynamicaccessor —](../../data/oledb/cdynamicaccessor-class.md) i trzeba zastąpić powiązania.  
  
 Aby uzyskać więcej informacji, zobacz [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)