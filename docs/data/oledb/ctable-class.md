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
ms.openlocfilehash: fab1ba2e496f4945eb56c0a67b833f6bf063404e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62368438"
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

*TAccessor*<br/>
Klasa metody dostępu.

*TRowset*<br/>
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

*Sesji*<br/>
[in] Sesja otwieraniu tabeli.

*wszTableName*<br/>
[in] Nazwa tabeli, aby otworzyć, jest przekazywany jako ciąg Unicode.

*szTableName*<br/>
[in] Nazwa tabeli, aby otworzyć, jest przekazywany jako ciąg ANSI.

*dbid*<br/>
[in] `DBID` Tabeli, aby otworzyć.

*pPropSet*<br/>
[in] Wskaźnik do tablicy [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) struktury zawierający właściwości i wartości do ustawienia. Zobacz [zestawy właściwości i właściwości grupy](/previous-versions/windows/desktop/ms713696(v=vs.85)) w *OLE DB Podręcznik programisty* w Windows SDK. Domyślna wartość NULL określa Brak właściwości.

*ulPropSets*<br/>
[in] Liczba [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) struktury przekazany *pPropSet* argumentu.

### <a name="return-value"></a>Wartość zwracana

Standardowa HRESULT.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [IOpenRowset::OpenRowset](/previous-versions/windows/desktop/ms716724(v=vs.85)) w *OLE DB Podręcznik programisty*.

## <a name="see-also"></a>Zobacz także

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)