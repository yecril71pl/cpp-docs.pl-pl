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
ms.openlocfilehash: ae4ceea53ec91cc3f9593dd3789fcf61e0702274
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376943"
---
# <a name="irowsetchangeimpl-class"></a>IRowsetChangeImpl — Klasa

Implementacja szablonów ole db interfejsu [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)) w specyfikacji OLE DB.

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

*T*<br/>
Klasa pochodząca `IRowsetChangeImpl`z .

*Storage*<br/>
Rekord użytkownika.

*BazaInterface*<br/>
Klasa podstawowa interfejsu, na `IRowsetChange`przykład .

*Klasa rowu*<br/>
Jednostka magazynowa dla uchwytu wiersza.

*Klasa mapy*<br/>
Jednostka magazynu dla wszystkich uchwytów wiersza posiadanych przez dostawcę.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldb.h

## <a name="members"></a>Elementy członkowskie

### <a name="interface-methods-used-with-irowsetchange"></a>Metody interfejsu (używane z IRowsetChange)

|||
|-|-|
|[Wychowania deleterow](#deleterows)|Usuwa wiersze z zestawu wierszy.|
|[Insertrow](#insertrow)|Wstawia wiersz do zestawu wierszy.|
|[Setdata](#setdata)|Ustawia wartości danych w jednej lub większej liczbie kolumn.|

### <a name="implementation-method-callback"></a>Metoda implementacji (wywołanie zwrotne)

|||
|-|-|
|[Flushdata](#flushdata)|Zastąpione przez dostawcę, aby zatwierdzić dane do magazynu.|

## <a name="remarks"></a>Uwagi

Ten interfejs jest odpowiedzialny za natychmiastowe operacje zapisu do magazynu danych. "Natychmiastowe" oznacza, że gdy użytkownik końcowy (osoba korzystająca z konsumenta) wprowadza jakiekolwiek zmiany, zmiany te są natychmiast przesyłane do magazynu danych (i nie można ich cofnąć).

`IRowsetChangeImpl`implementuje interfejs OLE `IRowsetChange` DB, który umożliwia aktualizowanie wartości kolumn w istniejących wierszach, usuwanie wierszy i wstawianie nowych wierszy.

Implementacja szablonów OLE DB obsługuje`SetData`wszystkie `InsertRow`metody `DeleteRows`podstawowe ( , , i ).

> [!IMPORTANT]
> Zdecydowanie zaleca się przeczytanie następującej dokumentacji PRZED podjęciem próby zaimplementowania dostawcy:

- [Tworzenie dostawcy podlegającego aktualizacji](../../data/oledb/creating-an-updatable-provider.md)

- Rozdział 6 *odniesienia dla programisty OLE DB*

- Zobacz również, `RUpdateRowset` jak klasa jest używana w przykładzie [UpdatePV.](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)

## <a name="irowsetchangeimpldeleterows"></a><a name="deleterows"></a>IRowsetChangeImpl::DeleteRows

Usuwa wiersze z zestawu wierszy.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (DeleteRows )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowsetChange::DeleteRows](/previous-versions/windows/desktop/ms724362(v=vs.85)) w *odwołaniu programisty OLE DB*.

## <a name="irowsetchangeimplinsertrow"></a><a name="insertrow"></a>IRowsetChangeImpl::InsertRow

Tworzy i inicjuje nowy wiersz w zestawie wierszy.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (InsertRow )(HCHAPTER /* hReserved */,
   HACCESSOR hAccessor,
   void* pData,
   HROW* phRow);
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowsetChange::InsertRow](/previous-versions/windows/desktop/ms716921(v=vs.85)) w *odwołaniu programisty OLE DB*.

## <a name="irowsetchangeimplsetdata"></a><a name="setdata"></a>IRowsetChangeImpl::SetData

Ustawia wartości danych w jednej lub większej liczbie kolumn.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>Parametry

Zobacz [IRowsetChange::SetData](/previous-versions/windows/desktop/ms721232(v=vs.85)) w *odwołaniu programisty OLE DB*.

## <a name="irowsetchangeimplflushdata"></a><a name="flushdata"></a>IRowsetChangeImpl::FlushData

Zastąpione przez dostawcę, aby zatwierdzić dane do magazynu.

### <a name="syntax"></a>Składnia

```cpp
HRESULT FlushData(HROW hRowToFlush,
   HACCESSOR hAccessorToFlush);
```

#### <a name="parameters"></a>Parametry

*hRowToFlush (hRowToFlush)*<br/>
[w] Dojście do wierszy dla danych. Typ tego wiersza jest określany na podstawie `IRowsetImpl` argumentu szablonu *RowClass* klasy (domyślnie).`CSimpleRow`

*hAccessorToFlush*<br/>
[w] Dojrzyj do akcesora, który `PROVIDER_MAP` zawiera informacje o powiązaniach i wpisz informacje w jego (zobacz [IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)).

### <a name="return-value"></a>Wartość zwracana

Standardowy HRESULT.

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
