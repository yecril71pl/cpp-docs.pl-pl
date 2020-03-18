---
title: CAccessorRowset — Klasa
ms.date: 11/04/2016
f1_keywords:
- CAccessorRowset
- ATL.CAccessorRowset
- ATL::CAccessorRowset
- CAccessorRowset.Bind
- CAccessorRowset::Bind
- CAccessorRowset::CAccessorRowset
- CAccessorRowset.CAccessorRowset
- ATL.CAccessorRowset.CAccessorRowset
- ATL::CAccessorRowset::CAccessorRowset
- CAccessorRowset.Close
- CAccessorRowset::Close
- CAccessorRowset::FreeRecordMemory
- CAccessorRowset.FreeRecordMemory
- CAccessorRowset.GetColumnInfo
- CAccessorRowset::GetColumnInfo
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
ms.openlocfilehash: 77c4eebae6ede5d74e24421cc4d3951c78e08777
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447274"
---
# <a name="caccessorrowset-class"></a>CAccessorRowset — Klasa

Hermetyzuje zestaw wierszy i skojarzone z nim metody dostępu w pojedynczej klasie.

## <a name="syntax"></a>Składnia

```cpp
template <class TAccessor = CNoAccessor,
   template <typename T> class TRowset = CRowset>
class CAccessorRowset : public TAccessor, public TRowset<TAccessor>
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

|||
|-|-|
|[Bind](#bind)|Tworzy powiązania (używane, gdy `bBind` jest określony jako **false** w [CCommand:: Open](../../data/oledb/ccommand-open.md)).|
|[CAccessorRowset](#caccessorrowset)|Konstruktor.|
|[Ściśle](#close)|Zamyka zestaw wierszy i wszelkie metody dostępu.|
|[FreeRecordMemory](#freerecordmemory)|Zwalnia wszystkie kolumny w bieżącym rekordzie, które muszą zostać zwolnione.|
|[GetColumnInfo](#getcolumninfo)|Implementuje [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)).|

## <a name="remarks"></a>Uwagi

Klasa `TAccessor` zarządza akcesorem. Klasa *TRowset* zarządza zestawem wierszy.

## <a name="bind"></a>CAccessorRowset:: bind

Tworzy powiązania, jeśli określono `bBind` jako **false** w [CCommand:: Open](../../data/oledb/ccommand-open.md).

### <a name="syntax"></a>Składnia

```cpp
HRESULT Bind();
```

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="caccessorrowset"></a>CAccessorRowset:: CAccessorRowset

Inicjuje obiekt `CAccessorRowset`.

### <a name="syntax"></a>Składnia

```cpp
CAccessorRowset();
```

## <a name="close"></a>CAccessorRowset:: Close

Zwalnia wszystkie aktywne metody dostępu i zestaw wierszy.

### <a name="syntax"></a>Składnia

```cpp
void Close();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie skojarzone pamięci.

## <a name="freerecordmemory"></a>CAccessorRowset:: FreeRecordMemory

Zwalnia wszystkie kolumny w bieżącym rekordzie, które muszą zostać zwolnione.

### <a name="syntax"></a>Składnia

```cpp
void FreeRecordMemory();
```

## <a name="getcolumninfo"></a>CAccessorRowset:: GetColumnInfo

Pobiera informacje o kolumnie z otwartego zestawu wierszy.

### <a name="syntax"></a>Składnia

```cpp
HRESULT GetColumnInfo(DBORDINAL* pulColumns,
   DBCOLUMNINFO** ppColumnInfo,
   LPOLESTR* ppStrings) const;

HRESULT GetColumnInfo(DBORDINAL* pColumns,
   DBCOLUMNINFO** ppColumnInfo);
```

#### <a name="parameters"></a>Parametry

Zobacz [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) w *dokumentacji programisty OLE DB*.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Użytkownik musi zwolnić zwrócone informacje o kolumnie i buforze ciągów. Użyj drugiej wersji tej metody, jeśli używasz [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) i chcesz zastąpić powiązania.

Aby uzyskać więcej informacji, zobacz [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) w *dokumentacji programisty OLE DB*.

## <a name="see-also"></a>Zobacz też

[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)