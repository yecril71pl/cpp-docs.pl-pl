---
title: Klasa CSession
ms.date: 11/04/2016
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
helpviewer_keywords:
- CSession class
- Abort method
- Close method
- Commit method
- GetTransactionInfo method
- Open method
- StartTransaction method
ms.assetid: 83cd798f-b45d-4f11-a23c-29183390450c
ms.openlocfilehash: 72797411b100480a06e27b71b000264070e57e32
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211136"
---
# <a name="csession-class"></a>Klasa CSession

Reprezentuje sesję dostępu pojedynczej bazy danych.

## <a name="syntax"></a>Składnia

```cpp
class CSession
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli. h

## <a name="members"></a>Members

### <a name="methods"></a>Metody

|||
|-|-|
|[Abort](#abort)|Anuluje (kończy) transakcję.|
|[Ściśle](#close)|Zamyka sesję.|
|[Zleca](#commit)|Zatwierdza transakcję.|
|[GetTransactionInfo](#gettransactioninfo)|Zwraca informacje dotyczące transakcji.|
|[Otwórz](#open)|Otwiera nową sesję dla obiektu źródła danych.|
|[StartTransaction](#starttransaction)|Rozpoczyna nową transakcję dla tej sesji.|

## <a name="remarks"></a>Uwagi

Co najmniej jedna sesja może być skojarzona z każdym połączeniem dostawcy (źródłem danych), które jest reprezentowane przez obiekt [CDataSource](../../data/oledb/cdatasource-class.md) . Aby utworzyć nowe `CSession` dla `CDataSource`, wywołaj [CSession:: Open](../../data/oledb/csession-open.md). Aby rozpocząć transakcję bazy danych, `CSession` zapewnia metodę `StartTransaction`. Po rozpoczęciu transakcji możesz zatwierdzić ją przy użyciu metody `Commit` lub anulować przy użyciu metody `Abort`.

## <a name="csessionabort"></a><a name="abort"></a>CSession:: Abort

Kończy transakcję.

### <a name="syntax"></a>Składnia

```cpp
HRESULT Abort(BOID* pboidReason = NULL,
   BOOL bRetaining = FALSE,
   BOOL bAsync = FALSE) const throw();
```

#### <a name="parameters"></a>Parametry

Zobacz [ITransaction:: Abort](/previous-versions/windows/desktop/ms709833(v=vs.85)) w *Kompendium OLE DB programisty*.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="csessionclose"></a><a name="close"></a>CSession:: Close

Zamyka sesję otwartą przez [CSession:: Open](../../data/oledb/csession-open.md).

### <a name="syntax"></a>Składnia

```cpp
void Close() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wskaźnik `m_spOpenRowset`.

## <a name="csessioncommit"></a><a name="commit"></a>CSession:: Commit

Zatwierdza transakcję.

### <a name="syntax"></a>Składnia

```cpp
HRESULT Commit(BOOL bRetaining = FALSE,
   DWORD grfTC = XACTTC_SYNC,
   DWORD grfRM = 0) const throw();
```

#### <a name="parameters"></a>Parametry

Zobacz [ITransaction:: Commit](/previous-versions/windows/desktop/ms713008(v=vs.85)) w *Kompendium OLE DB programisty*.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [ITransaction:: Commit](/previous-versions/windows/desktop/ms713008(v=vs.85)).

## <a name="csessiongettransactioninfo"></a><a name="gettransactioninfo"></a>CSession:: GetTransactionInfo

Zwraca informacje dotyczące transakcji.

### <a name="syntax"></a>Składnia

```cpp
HRESULT GetTransactionInfo(XACTTRANSINFO* pInfo) const throw();
```

#### <a name="parameters"></a>Parametry

Zobacz [ITransaction:: GetTransactionInfo](/previous-versions/windows/desktop/ms714975(v=vs.85)) w *dokumentacji programisty OLE DB*.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [ITransaction:: GetTransactionInfo](/previous-versions/windows/desktop/ms714975(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="csessionopen"></a><a name="open"></a>CSession:: Open

Otwiera nową sesję dla obiektu źródła danych.

### <a name="syntax"></a>Składnia

```cpp
HRESULT Open(const CDataSource& ds,
   DBPROPSET *pPropSet = NULL,
   ULONG ulPropSets = 0) throw();
```

#### <a name="parameters"></a>Parametry

*domenowe*<br/>
podczas Źródło danych, dla którego ma zostać otwarta sesja.

*pPropSet*<br/>
podczas Wskaźnik do tablicy struktur [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) zawierających właściwości i wartości, które mają zostać ustawione. Zobacz [zestawy właściwości i grupy właściwości](/previous-versions/windows/desktop/ms713696(v=vs.85)) w *odniesieniu do OLE DB programisty* w Windows SDK.

*ulPropSets*<br/>
podczas Liczba struktur [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) przeniesiona w argumencie *pPropSet* .

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Należy otworzyć obiekt źródła danych przy użyciu [CDataSource:: Open](../../data/oledb/cdatasource-open.md) przed przekazaniem go do `CSession::Open`.

## <a name="csessionstarttransaction"></a><a name="starttransaction"></a>CSession:: StartTransaction

Rozpoczyna nową transakcję dla tej sesji.

### <a name="syntax"></a>Składnia

```cpp
HRESULT StartTransaction(ISOLEVEL isoLevel = ISOLATIONLEVEL_READCOMMITTED,
   ULONG isoFlags = 0,
   ITransactionOptions* pOtherOptions = NULL,
   ULONG* pulTransactionLevel = NULL) const throw();
```

#### <a name="parameters"></a>Parametry

Zobacz [ITransactionLocal:: StartTransaction](/previous-versions/windows/desktop/ms709786(v=vs.85)) w *dokumentacji programisty OLE DB*.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [ITransactionLocal:: StartTransaction](/previous-versions/windows/desktop/ms709786(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="see-also"></a>Zobacz też

[CatDB](../../overview/visual-cpp-samples.md)<br/>
[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)
