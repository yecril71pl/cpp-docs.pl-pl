---
title: ICommandImpl — Klasa
ms.date: 11/04/2016
f1_keywords:
- ICommandImpl
- ICommandImpl::Cancel
- Cancel
- ICommandImpl.Cancel
- ICommandImpl::CancelExecution
- ATL::ICommandImpl::CancelExecution
- ATL.ICommandImpl.CancelExecution
- CancelExecution
- ICommandImpl.CancelExecution
- ICommandImpl::CreateRowset
- ICommandImpl.CreateRowset
- CreateRowset
- ICommandImpl::Execute
- ICommandImpl.Execute
- ICommandImpl::GetDBSession
- GetDBSession
- ICommandImpl.GetDBSession
- ATL.ICommandImpl.ICommandImpl
- ATL::ICommandImpl::ICommandImpl
- ICommandImpl::ICommandImpl
- ICommandImpl.ICommandImpl
- ICommandImpl::m_bCancel
- ICommandImpl.m_bCancel
- m_bCancel
- ATL::ICommandImpl::m_bCancel
- ATL.ICommandImpl.m_bCancel
- ICommandImpl::m_bCancelWhenExecuting
- ICommandImpl.m_bCancelWhenExecuting
- ATL::ICommandImpl::m_bCancelWhenExecuting
- m_bCancelWhenExecuting
- ATL.ICommandImpl.m_bCancelWhenExecuting
- ICommandImpl.m_bIsExecuting
- ATL::ICommandImpl::m_bIsExecuting
- m_bIsExecuting
- ATL.ICommandImpl.m_bIsExecuting
- ICommandImpl::m_bIsExecuting
helpviewer_keywords:
- ICommandImpl class
- Cancel method
- CancelExecution method
- CreateRowset method
- Execute method
- GetDBSession method
- ICommandImpl constructor
- ICommandImpl class, constructor
- m_bCancel
- m_bCancelWhenExecuting
- m_bIsExecuting
ms.assetid: ef285fef-0d66-45e6-a762-b03357098e3b
ms.openlocfilehash: 2f2d3938d63e5e67fc501d52d269c06f6b144ac8
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501824"
---
# <a name="icommandimpl-class"></a>ICommandImpl — Klasa

Zapewnia implementację interfejsu [Interfejs ICommand](/previous-versions/windows/desktop/ms709737(v=vs.85)) .

## <a name="syntax"></a>Składnia

```cpp
template <class T, class CommandBase = ICommand>
class ATL_NO_VTABLE ICommandImpl : public CommandBase
```

### <a name="parameters"></a>Parametry

*T*<br/>
Klasa, która pochodzi od `ICommandImpl` .

*CommandBase*<br/>
Interfejs polecenia. Wartość domyślna to `ICommand`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** ATLDB. h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

| Nazwa | Opis |
|-|-|
|[Anuluj](#cancel)|Anuluje bieżące wykonanie polecenia.|
|[CancelExecution](#cancelexecution)|Anuluje bieżące wykonanie polecenia.|
|[CreateRowset](#createrowset)|Tworzy obiekt zestawu wierszy.|
|[Wykonaj polecenie](#execute)|Wykonuje polecenie.|
|[GetDBSession](#getdbsession)|Zwraca wskaźnik interfejsu do sesji, która utworzyła polecenie.|
|[ICommandImpl](#icommandimpl)|Konstruktor.|

### <a name="data-members"></a>Elementy członkowskie danych

| Nazwa | Opis |
|-|-|
|[m_bCancel](#bcancel)|Wskazuje, czy polecenie ma być anulowane.|
|[m_bCancelWhenExecuting](#bcancelwhenexecuting)|Wskazuje, czy polecenie ma zostać anulowane podczas wykonywania.|
|[m_bIsExecuting](#bisexecuting)|Wskazuje, czy polecenie jest aktualnie wykonywane.|

## <a name="remarks"></a>Uwagi

Obowiązkowy interfejs w obiekcie Command.

## <a name="icommandimplcancel"></a><a name="cancel"></a> ICommandImpl:: Cancel

Anuluje bieżące wykonanie polecenia.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(Cancel)();
```

### <a name="remarks"></a>Uwagi

Zobacz [Interfejs ICommand:: Cancel](/previous-versions/windows/desktop/ms714402(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="icommandimplcancelexecution"></a><a name="cancelexecution"></a> ICommandImpl:: CancelExecution

Anuluje bieżące wykonanie polecenia.

### <a name="syntax"></a>Składnia

```cpp
HRESULT CancelExecution();
```

## <a name="icommandimplcreaterowset"></a><a name="createrowset"></a> ICommandImpl:: isrowset

Wywoływane przez [Execute](#execute) , aby utworzyć pojedynczy zestaw wierszy.

### <a name="syntax"></a>Składnia

```cpp
template template <class RowsetClass>
HRESULT CreateRowset(IUnknown* pUnkOuter,
   REFIID riid,
   DBPARAMS* pParams,
   DBROWCOUNT* pcRowsAffected,
   IUnknown** ppRowset,
   RowsetClass*& pRowsetObj);
```

#### <a name="parameters"></a>Parametry

*RowsetClass*<br/>
Składowa klasy szablonu reprezentująca klasę zestawu wierszy użytkownika. Zwykle generowany przez kreatora.

*pUnkOuter*<br/>
podczas Wskaźnik do interfejsu kontrolującego, `IUnknown` Jeśli zestaw wierszy jest tworzony w ramach agregacji; w przeciwnym razie ma wartość null.

*riid*<br/>
podczas Odnosi się do *riid* w `ICommand::Execute` .

*pParams*<br/>
[we/out] Odnosi się do *pParams* w `ICommand::Execute` .

*pcRowsAffected*<br/>
Odnosi się do *pcRowsAffected* w `ICommand::Execute` .

*ppRowset*<br/>
[we/out] Odnosi się do *ppRowset* w `ICommand::Execute` .

*pRowsetObj*<br/>
określoną Wskaźnik do obiektu zestawu wierszy. Zazwyczaj ten parametr nie jest używany, ale może być używany, jeśli trzeba wykonać więcej pracy na zestawie wierszy przed przekazaniem go do obiektu COM. Okres istnienia *pRowsetObj* jest związany z *ppRowset*.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT. `ICommand::Execute`Aby uzyskać listę typowych wartości, zobacz.

### <a name="remarks"></a>Uwagi

Aby utworzyć więcej niż jeden zestaw wierszy lub podać własne warunki tworzenia różnych zestawów wierszy, umieść różne wywołania do `CreateRowset` wewnątrz `Execute` .

Zobacz [Interfejs ICommand:: Execute](/previous-versions/windows/desktop/ms718095(v=vs.85)) w *dokumentacji programisty OLE DB.*

## <a name="icommandimplexecute"></a><a name="execute"></a> ICommandImpl:: Execute

Wykonuje polecenie.

### <a name="syntax"></a>Składnia

```cpp
HRESULT Execute(IUnknown* pUnkOuter,
   REFIID riid,
   DBPARAMS* pParams,
   DBROWCOUNT* pcRowsAffected,
   IUnknown** ppRowset);
```

#### <a name="parameters"></a>Parametry

Zobacz [Interfejs ICommand:: Execute](/previous-versions/windows/desktop/ms718095(v=vs.85)) w *dokumentacji programisty OLE DB*.

### <a name="remarks"></a>Uwagi

Żądany interfejs wychodzący będzie interfejsem uzyskanym z obiektu zestawu wierszy, który tworzy ta funkcja.

`Execute` wywołuje [zestaw wierszy](#createrowset). Zastąp domyślną implementację, aby utworzyć więcej niż jeden zestaw wierszy lub podać własne warunki tworzenia różnych zestawów wierszy.

## <a name="icommandimplgetdbsession"></a><a name="getdbsession"></a> ICommandImpl:: GetDBSession

Zwraca wskaźnik interfejsu do sesji, która utworzyła polecenie.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (GetDBSession) (REFIID riid,
   IUnknown** ppSession);
```

#### <a name="parameters"></a>Parametry

Zobacz [Interfejs ICommand:: GetDBSession](/previous-versions/windows/desktop/ms719622(v=vs.85)) w *dokumentacji programisty OLE DB*.

### <a name="remarks"></a>Uwagi

Przydatne do pobierania właściwości z sesji.

## <a name="icommandimplicommandimpl"></a><a name="icommandimpl"></a> ICommandImpl:: ICommandImpl

Konstruktor.

### <a name="syntax"></a>Składnia

```cpp
ICommandImpl();
```

## <a name="icommandimplm_bcancel"></a><a name="bcancel"></a> ICommandImpl:: m_bCancel

Wskazuje, czy polecenie zostało anulowane.

### <a name="syntax"></a>Składnia

```cpp
unsigned m_bCancel:1;
```

### <a name="remarks"></a>Uwagi

Tę zmienną można pobrać w `Execute` metodzie klasy Command i anulować zgodnie z potrzebami.

## <a name="icommandimplm_bcancelwhenexecuting"></a><a name="bcancelwhenexecuting"></a> ICommandImpl:: m_bCancelWhenExecuting

Wskazuje, czy polecenie może zostać anulowane podczas wykonywania.

### <a name="syntax"></a>Składnia

```cpp
unsigned m_bCancelWhenExecuting:1;
```

### <a name="remarks"></a>Uwagi

Wartość domyślna **`true`** (może być anulowana).

## <a name="icommandimplm_bisexecuting"></a><a name="bisexecuting"></a> ICommandImpl:: m_bIsExecuting

Wskazuje, czy polecenie jest aktualnie wykonywane.

### <a name="syntax"></a>Składnia

```cpp
unsigned m_bIsExecuting:1;
```

### <a name="remarks"></a>Uwagi

`Execute`Metoda klasy Command może ustawić tę zmienną na **`true`** .

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
