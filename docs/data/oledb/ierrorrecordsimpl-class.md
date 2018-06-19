---
title: Ierrorrecordsimpl — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IErrorRecordsImpl
- ATL.IErrorRecordsImpl
- IErrorRecordsImpl
dev_langs:
- C++
helpviewer_keywords:
- IErrorRecordsImpl class
ms.assetid: dea8e938-c5d8-45ab-86de-eb8fbf534ffb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0d0425e7765cf09abb870cb39720cf43c8c74174
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33105468"
---
# <a name="ierrorrecordsimpl-class"></a>IErrorRecordsImpl — Klasa
Implementuje OLE DB [IErrorRecords](https://msdn.microsoft.com/en-us/library/ms718112.aspx) interfejsu, dodawanie rekordów i pobieranie rekordów z elementem członkowskim danych ([m_rgErrors](../../data/oledb/ierrorrecordsimpl-m-rgerrors.md)) typu **CAtlArray <** `RecordClass`**>**.  
  
## <a name="syntax"></a>Składnia

```cpp
template <class T, class RecordClass = ATLERRORINFO>  
class IErrorRecordsImpl : public IErrorRecords  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Klasa pochodna od `IErrorRecordsImpl`.  
  
 `RecordClass`  
 Klasa, która reprezentuje obiekt błąd OLE DB.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[GetErrorDescriptionString](../../data/oledb/ierrorrecordsimpl-geterrordescriptionstring.md)|Pobiera ciąg opisu błędu z rekord błędu.|  
|[GetErrorGUID](../../data/oledb/ierrorrecordsimpl-geterrorguid.md)|Pobiera błąd identyfikatora GUID z rekord błędu.|  
|[GetErrorHelpContext](../../data/oledb/ierrorrecordsimpl-geterrorhelpcontext.md)|Pobiera identyfikator kontekstu pomocy z rekord błędu.|  
|[GetErrorHelpFile](../../data/oledb/ierrorrecordsimpl-geterrorhelpfile.md)|Pobiera pełną nazwę ścieżki pliku pomocy z rekord błędu.|  
|[GetErrorSource](../../data/oledb/ierrorrecordsimpl-geterrorsource.md)|Pobiera błąd kodu źródłowego z rekord błędu.|  
  
### <a name="interface-methods"></a>Metody interfejsu  
  
|||  
|-|-|  
|[AddErrorRecord](../../data/oledb/ierrorrecordsimpl-adderrorrecord.md)|Dodaje rekord obiektu błąd OLE DB.|  
|[GetBasicErrorInfo](../../data/oledb/cdberrorinfo-getbasicerrorinfo.md)|Zwraca podstawowe informacje o błędzie, takie jak kod powrotny i numer błędu specyficznego dla dostawcy.|  
|[GetCustomErrorObject](../../data/oledb/cdberrorinfo-getcustomerrorobject.md)|Zwraca wskaźnik do interfejsu w obiekcie błędu niestandardowego.|  
|[GetErrorInfo](../../data/oledb/cdberrorinfo-geterrorinfo.md)|Zwraca [IErrorInfo](https://msdn.microsoft.com/en-us/library/ms718112.aspx) wskaźnika interfejsu na określony rekord.|  
|[GetErrorParameters](../../data/oledb/cdberrorinfo-geterrorparameters.md)|Zwraca parametry błędów.|  
|[GetRecordCount](../../mfc/reference/cdaorecordset-class.md#getrecordcount)|Zwraca liczbę rekordów w obiekcie rekordów OLE DB.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|||  
|-|-|  
|[m_rgErrors](../../data/oledb/ierrorrecordsimpl-m-rgerrors.md)|Tablica rekordów błędów.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)