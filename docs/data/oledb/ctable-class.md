---
title: Klasa CTable
ms.date: 11/04/2016
f1_keywords:
- ATL::CTable
- ATL.CTable
- CTable
- ATL.CTable.Open
- ATL::CTable::Open
- CTable::Open
- CTable.Open
helpviewer_keywords:
- CTable class
- Open method
ms.assetid: f13fdaa3-e198-4557-977d-54b0bbc3454d
ms.openlocfilehash: a967ef8fa2832afd56442ae4f988ba080d0b2872
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845643"
---
# <a name="ctable-class"></a>Klasa CTable

Zapewnia metodę bezpośredniego dostępu do prostego zestawu wierszy (jeden bez parametrów).

## <a name="syntax"></a>Składnia

```cpp
template <class TAccessor = CNoAccessor,
            template <typename T> class TRowset = CRowset>
class CTable :
   public CAccessorRowset <TAccessor, TRowset>
```

### <a name="parameters"></a>Parametry

*TAccessor*<br/>
Klasa akcesora.

*TRowset*<br/>
Klasa zestawu wierszy.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli. h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

| Nazwa | Opis |
|-|-|
|[Otwórz](#open)|Otwiera tabelę.|

## <a name="remarks"></a>Uwagi

Zobacz [CCommand](../../data/oledb/ccommand-class.md) , aby uzyskać informacje na temat wykonywania polecenia w celu uzyskania dostępu do zestawu wierszy.

## <a name="ctableopen"></a><a name="open"></a> CTable:: Open

Otwiera tabelę.

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

*obrad*<br/>
podczas Sesja, dla której tabela jest otwarta.

*wszTableName*<br/>
podczas Nazwa tabeli, która ma zostać otwarta, przeniesiona jako ciąg Unicode.

*szTableName*<br/>
podczas Nazwa tabeli do otwarcia, która została przeniesiona jako ciąg ANSI.

*DBID*<br/>
podczas `DBID` Tabela, która ma zostać otwarta.

*pPropSet*<br/>
podczas Wskaźnik do tablicy struktur [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) zawierających właściwości i wartości, które mają zostać ustawione. Zobacz [zestawy właściwości i grupy właściwości](/previous-versions/windows/desktop/ms713696(v=vs.85)) w *odniesieniu do OLE DB programisty* w Windows SDK. Wartość domyślna NULL określa brak właściwości.

*ulPropSets*<br/>
podczas Liczba struktur [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) przeniesiona w argumencie *pPropSet* .

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [IOpenRowset:: OPENROWSET](/previous-versions/windows/desktop/ms716724(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="see-also"></a>Zobacz też

[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Dokumentacja szablonów klientów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
