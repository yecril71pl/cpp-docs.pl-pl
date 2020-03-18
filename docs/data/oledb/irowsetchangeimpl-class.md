---
title: IRowsetChangeImpl — Klasa
ms.date: 11/04/2016
f1_keywords:
- ATL::IRowsetChangeImpl
- IRowsetChangeImpl
- ATL.IRowsetChangeImpl
- ATL.IRowsetChangeImpl.DeleteRows
- ATL::IRowsetChangeImpl::DeleteRows
- IRowsetChangeImpl.DeleteRows
- DeleteRows
- IRowsetChangeImpl::DeleteRows
- ATL.IRowsetChangeImpl.InsertRow
- InsertRow
- IRowsetChangeImpl.InsertRow
- ATL::IRowsetChangeImpl::InsertRow
- IRowsetChangeImpl::InsertRow
- IRowsetChangeImpl::SetData
- ATL.IRowsetChangeImpl.SetData
- IRowsetChangeImpl.SetData
- ATL::IRowsetChangeImpl::SetData
- IRowsetChangeImpl::FlushData
- IRowsetChangeImpl.FlushData
- FlushData
helpviewer_keywords:
- providers, updatable
- updatable providers, immediate update
- IRowsetChangeImpl class
- DeleteRows method
- InsertRow method
- SetData method
- FlushData method
ms.assetid: 1e9fee15-ed9e-4387-af8f-215569beca6c
ms.openlocfilehash: 1e07289a2d0fb283a20657797db5f915c06a39ad
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446325"
---
# <a name="irowsetchangeimpl-class"></a>IRowsetChangeImpl — Klasa

Implementacja szablonów OLE DB interfejsu [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)) w specyfikacji OLE DB.

## <a name="syntax"></a>Składnia

```cpp
template <
   class T,
   class Storage,
   class BaseInterface = IRowsetChange,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>>
class ATL_NO_VTABLE IRowsetChangeImpl : public BaseInterface
```

### <a name="parameters"></a>Parametry

*&*<br/>
Klasa pochodna `IRowsetChangeImpl`.

*Storage*<br/>
Rekord użytkownika.

*BaseInterface*<br/>
Klasa bazowa dla interfejsu, taka jak `IRowsetChange`.

*RowClass*<br/>
Jednostka magazynowa dla uchwytu wiersza.

*MapClass*<br/>
Jednostka magazynowa dla wszystkich dojść wiersza przechowywanych przez dostawcę.

## <a name="requirements"></a>Wymagania

**Nagłówek:** ATLDB. h

## <a name="members"></a>Elementy członkowskie

### <a name="interface-methods-used-with-irowsetchange"></a>Metody interfejsu (używane z IRowsetChange)

|||
|-|-|
|[DeleteRows](#deleterows)|Usuwa wiersze z zestawu wierszy.|
|[InsertRow](#insertrow)|Wstawia wiersz do zestawu wierszy.|
|[Operację](#setdata)|Ustawia wartości danych w co najmniej jednej kolumnie.|

### <a name="implementation-method-callback"></a>Implementacja — Metoda (wywołanie zwrotne)

|||
|-|-|
|[FlushData](#flushdata)|Przesłonięte przez dostawcę, aby zatwierdzić dane do swojego magazynu.|

## <a name="remarks"></a>Uwagi

Ten interfejs jest odpowiedzialny za natychmiastowe operacje zapisu w magazynie danych. "Natychmiastowe" oznacza, że gdy użytkownik końcowy (osoba korzystająca z konsumenta) wprowadza zmiany, te zmiany są natychmiast przesyłane do magazynu danych (i nie można ich cofnąć).

`IRowsetChangeImpl` implementuje interfejs OLE DB `IRowsetChange`, który umożliwia aktualizowanie wartości kolumn w istniejących wierszach, usuwanie wierszy i wstawianie nowych wierszy.

Implementacja szablonów OLE DB obsługuje wszystkie metody podstawowe (`SetData`, `InsertRow`i `DeleteRows`).

> [!IMPORTANT]
>  PRZED podjęciem próby wdrożenia dostawcy zdecydowanie zalecamy zapoznanie się z poniższą dokumentacją:

- [Tworzenie aktualizowalnego dostawcy](../../data/oledb/creating-an-updatable-provider.md)

- Rozdział 6 *odwołania programisty OLE DB*

- Zobacz również, jak Klasa `RUpdateRowset` jest używana w przykładzie [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) .

## <a name="deleterows"></a>IRowsetChangeImpl::D eleteRows

Usuwa wiersze z zestawu wierszy.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (DeleteRows )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowsetChange::D eleterows](/previous-versions/windows/desktop/ms724362(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="insertrow"></a>IRowsetChangeImpl:: InsertRow

Tworzy i inicjuje nowy wiersz w zestawie wierszy.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (InsertRow )(HCHAPTER /* hReserved */,
   HACCESSOR hAccessor,
   void* pData,
   HROW* phRow);
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowsetChange:: InsertRow](/previous-versions/windows/desktop/ms716921(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="setdata"></a>IRowsetChangeImpl:: SetData

Ustawia wartości danych w co najmniej jednej kolumnie.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowsetChange:: SetData](/previous-versions/windows/desktop/ms721232(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="flushdata"></a>IRowsetChangeImpl:: FlushData

Przesłonięte przez dostawcę, aby zatwierdzić dane do swojego magazynu.

### <a name="syntax"></a>Składnia

```cpp
HRESULT FlushData(HROW hRowToFlush,
   HACCESSOR hAccessorToFlush);
```

#### <a name="parameters"></a>Parametry

*hRowToFlush*<br/>
podczas Dojście do wierszy danych. Typ tego wiersza jest określany na podstawie argumentu szablonu *RowClass* klasy `IRowsetImpl` (domyślnie`CSimpleRow`).

*hAccessorToFlush*<br/>
podczas Dojście do metody dostępu, która zawiera informacje o powiązaniu i informacje o typie w jego `PROVIDER_MAP` (zobacz [IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)).

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)