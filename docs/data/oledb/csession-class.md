---
title: Klasa CSession | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CSession
- ATL::CSession
- ATL.CSession
- CSession.Abort
- CSession::Abort
- ATL.CSession.Abort
- ATL::CSession::Abort
- CSession::Close
- ATL.CSession.Close
- CSession.Close
- ATL::CSession::Close
- CSession.Commit
- ATL.CSession.Commit
- ATL::CSession::Commit
- CSession::Commit
- GetTransactionInfo
- CSession.GetTransactionInfo
- ATL.CSession.GetTransactionInfo
- CSession::GetTransactionInfo
- ATL::CSession::GetTransactionInfo
- ATL::CSession::Open
- CSession::Open
- CSession.Open
- ATL.CSession.Open
- CSession::StartTransaction
- StartTransaction
- ATL.CSession.StartTransaction
- CSession.StartTransaction
- ATL::CSession::StartTransaction
dev_langs:
- C++
helpviewer_keywords:
- CSession class
- Abort method
- Close method
- Commit method
- GetTransactionInfo method
- Open method
- StartTransaction method
ms.assetid: 83cd798f-b45d-4f11-a23c-29183390450c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8cbfa7dc712755790b3a398db3377a8faccd4525
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2018
ms.locfileid: "49084025"
---
# <a name="csession-class"></a>Klasa CSession

Reprezentuje sesję dostępu do pojedynczej bazy danych.  
  
## <a name="syntax"></a>Składnia

```cpp
class CSession  
```  

## <a name="requirements"></a>Wymagania  

**Nagłówek:** atldbcli.h  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Abort](#abort)|Anuluje (kończy) transakcji.|  
|[Zamknij](#close)|Zamyka sesję.|  
|[Zatwierdzenia](#commit)|zatwierdzeń transakcji.|  
|[GetTransactionInfo](#gettransactioninfo)|Zwraca informacje dotyczące transakcji.|  
|[Otwórz](#open)|Otwiera nową sesję dla obiektu źródła danych.|  
|[Starttransaction —](#starttransaction)|Rozpoczyna się nowej transakcji dla tej sesji.|  
  
## <a name="remarks"></a>Uwagi  

Co najmniej jednej sesji może być skojarzona z każdego połączenia dostawcy (źródła danych), która jest reprezentowana przez [CDataSource](../../data/oledb/cdatasource-class.md) obiektu. Aby utworzyć nowy `CSession` dla `CDataSource`, wywołaj [CSession::Open](../../data/oledb/csession-open.md). Aby rozpocząć transakcji bazy danych, `CSession` zapewnia `StartTransaction` metody. Po rozpoczęciu transakcji możesz zatwierdzić do niego przy użyciu `Commit` metodę, lub Anuluj ją przy użyciu `Abort` metody.  
  
## <a name="abort"></a> CSession::Abort

Przerywa transakcję.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Abort(BOID* pboidReason = NULL,   
   BOOL bRetaining = FALSE,   
   BOOL bAsync = FALSE) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  

Zobacz [ITransaction::Abort](/previous-versions/windows/desktop/ms709833) w *OLE DB Podręcznik programisty*.  
  
### <a name="return-value"></a>Wartość zwracana  

Standardowa HRESULT. 

## <a name="close"></a> CSession::Close

Zamyka sesję, który został otworzony [CSession::Open](../../data/oledb/csession-open.md).  
  
### <a name="syntax"></a>Składnia  
  
```cpp
void Close() throw();  
```  
  
### <a name="remarks"></a>Uwagi  

Wersje `m_spOpenRowset` wskaźnika.  

## <a name="commit"></a> CSession::Commit

zatwierdzeń transakcji.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Commit(BOOL bRetaining = FALSE,   
   DWORD grfTC = XACTTC_SYNC,   
   DWORD grfRM = 0) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  

Zobacz [metody ITransaction::Commit](/previous-versions/windows/desktop/ms713008) w *OLE DB Podręcznik programisty*.  
  
### <a name="return-value"></a>Wartość zwracana  

Standardowa HRESULT.  
  
### <a name="remarks"></a>Uwagi  

Aby uzyskać więcej informacji, zobacz [metody ITransaction::Commit](/previous-versions/windows/desktop/ms713008).  

## <a name="gettransactioninfo"></a> CSession::GetTransactionInfo

Zwraca informacje dotyczące transakcji.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetTransactionInfo(XACTTRANSINFO* pInfo) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  

Zobacz [ITransaction::GetTransactionInfo](/previous-versions/windows/desktop/ms714975) w *OLE DB Podręcznik programisty*.  
  
### <a name="return-value"></a>Wartość zwracana  

Standardowa HRESULT.  
  
### <a name="remarks"></a>Uwagi  

Aby uzyskać więcej informacji, zobacz [ITransaction::GetTransactionInfo](/previous-versions/windows/desktop/ms714975) w *OLE DB Podręcznik programisty*. 

## <a name="open"></a> CSession::Open

Otwiera nową sesję dla obiektu źródła danych.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Open(const CDataSource& ds,  
   DBPROPSET *pPropSet = NULL,  
   ULONG ulPropSets = 0) throw();  
```  
  
#### <a name="parameters"></a>Parametry  

*ds*<br/>
[in] Źródło danych, dla którego ma zostać otwarte sesji.  
  
*pPropSet*<br/>
[in] Wskaźnik do tablicy [DBPROPSET](/previous-versions/windows/desktop/ms714367) struktury zawierający właściwości i wartości do ustawienia. Zobacz [zestawy właściwości i właściwości grupy](/previous-versions/windows/desktop/ms713696) w *OLE DB Podręcznik programisty* w Windows SDK.  
  
*ulPropSets*<br/>
[in] Liczba [DBPROPSET](/previous-versions/windows/desktop/ms714367) struktury przekazany *pPropSet* argumentu.  
  
### <a name="return-value"></a>Wartość zwracana  

Standardowa HRESULT.  
  
### <a name="remarks"></a>Uwagi  

Należy otworzyć źródła danych obiektu przy użyciu [CDataSource::Open](../../data/oledb/cdatasource-open.md) przed przekazaniem go do `CSession::Open`.  

## <a name="starttransaction"></a> CSession::StartTransaction

Rozpoczyna się nowej transakcji dla tej sesji.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT StartTransaction(ISOLEVEL isoLevel = ISOLATIONLEVEL_READCOMMITTED,  
   ULONG isoFlags = 0,  
   ITransactionOptions* pOtherOptions = NULL,  
   ULONG* pulTransactionLevel = NULL) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  

Zobacz [ITransactionLocal::StartTransaction](/previous-versions/windows/desktop/ms709786) w *OLE DB Podręcznik programisty*.  
  
### <a name="return-value"></a>Wartość zwracana  

Standardowa HRESULT.  
  
### <a name="remarks"></a>Uwagi  

Aby uzyskać więcej informacji, zobacz [ITransactionLocal::StartTransaction](/previous-versions/windows/desktop/ms709786) w *OLE DB Podręcznik programisty*. 
  
## <a name="see-also"></a>Zobacz też  

[CatDB](../../visual-cpp-samples.md)<br/>
[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)