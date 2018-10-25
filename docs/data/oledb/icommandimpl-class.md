---
title: Icommandimpl — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
- ICommandImpl
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 91b273e8bfda6c050fa3d9d6db7aafffbe03d684
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077624"
---
# <a name="icommandimpl-class"></a>ICommandImpl — Klasa

Udostępnia implementację dla [ICommand](/previous-versions/windows/desktop/ms709737) interfejsu.

## <a name="syntax"></a>Składnia

```cpp
template <class T, class CommandBase = ICommand>
class ATL_NO_VTABLE ICommandImpl : public CommandBase
```

### <a name="parameters"></a>Parametry

*T*<br/>
Z klasą pochodną `ICommandImpl`.

*CommandBase*<br/>
Interfejs polecenia. Wartość domyślna to `ICommand`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldb.h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[Anulowanie](#cancel)|Anuluje bieżące wykonywanie polecenia.|
|[CancelExecution](#cancelexecution)|Anuluje bieżące wykonywanie polecenia.|
|[Createrowset —](#createrowset)|Tworzy obiekt zestawu wierszy.|
|[Execute](#execute)|Wykonuje polecenie.|
|[GetDBSession](#getdbsession)|Zwraca wskaźnik interfejsu do sesja, która utworzyła polecenia.|
|[Icommandimpl —](#icommandimpl)|Konstruktor.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|[m_bCancel](#bcancel)|Wskazuje, czy polecenie ma zostać anulowana.|
|[m_bCancelWhenExecuting](#bcancelwhenexecuting)|Wskazuje, czy ma być anulowane podczas wykonywania polecenia.|
|[m_bIsExecuting](#bisexecuting)|Wskazuje, czy polecenie jest w trakcie wykonywania.|

## <a name="remarks"></a>Uwagi

Obowiązkowego interfejsu dla obiektu polecenia.

## <a name="cancel"></a> ICommandImpl::Cancel

Anuluje bieżące wykonywanie polecenia.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(Cancel)();
```

### <a name="remarks"></a>Uwagi

Zobacz [ICommand::Cancel](/previous-versions/windows/desktop/ms714402) w *OLE DB Podręcznik programisty*.

## <a name="cancelexecution"></a> ICommandImpl::CancelExecution

Anuluje bieżące wykonywanie polecenia.

### <a name="syntax"></a>Składnia

```cpp
HRESULT CancelExecution();
```

## <a name="createrowset"></a> ICommandImpl::CreateRowset

Wywoływane przez [Execute](../../data/oledb/icommandimpl-execute.md) do utworzenia pojedynczego zestawu wierszy.

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
Składowa klasy szablonu reprezentująca klasy zestawów wierszy przez użytkownika. Zwykle generowane przez kreatora.

*pUnkOuter*<br/>
[in] Wskaźnik do kontrolowania `IUnknown` interfejsu, jeśli zestaw wierszy jest tworzony jako część agregacji; w przeciwnym razie ma wartość null.

*Parametr riid*<br/>
[in] Odnosi się do *riid* w `ICommand::Execute`.

*pParams*<br/>
[/ Ściemnianie] Odnosi się do *pParams* w `ICommand::Execute`.

*pcRowsAffected*<br/>
Odnosi się do *pcRowsAffected* w `ICommand::Execute`.

*ppRowset*<br/>
[/ Ściemnianie] Odnosi się do *ppRowset* w `ICommand::Execute`.

*pRowsetObj*<br/>
[out] Wskaźnik do obiektu zestawu wierszy. Zazwyczaj ten parametr nie jest używany, ale mogą używane, jeśli konieczne jest przeprowadzenie więcej pracy na zestawie wierszy przed przekazaniem go do obiektu COM. Okres istnienia *pRowsetObj* jest ograniczone przez *ppRowset*.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT. Zobacz `ICommand::Execute` listę typowe wartości.

### <a name="remarks"></a>Uwagi

Aby utworzyć więcej niż jeden zestaw wierszy lub podać warunki do tworzenia różnych zestawów wierszy, wywołania różnych `CreateRowset` z poziomu `Execute`.

Zobacz [ICommand::Execute](/previous-versions/windows/desktop/ms718095) w *OLE DB Podręcznik programisty.*

## <a name="execute"></a> ICommandImpl::Execute

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

Zobacz [ICommand::Execute](/previous-versions/windows/desktop/ms718095) w *OLE DB Podręcznik programisty*.

### <a name="remarks"></a>Uwagi

Żądany interfejs wychodzących będą interfejs uzyskanych z obiektu zestawu wierszy, który tworzy tę funkcję.

`Execute` wywołania [createrowset —](../../data/oledb/icommandimpl-createrowset.md). Musi zostać zastąpiona w implementacji domyślnej, aby utworzyć więcej niż jeden zestaw wierszy lub podać warunki do tworzenia różnych zestawów wierszy.

## <a name="getdbsession"></a> ICommandImpl::GetDBSession

Zwraca wskaźnik interfejsu do sesja, która utworzyła polecenia.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD (GetDBSession) (REFIID riid,
   IUnknown** ppSession);
```

#### <a name="parameters"></a>Parametry

Zobacz [ICommand::GetDBSession](/previous-versions/windows/desktop/ms719622) w *OLE DB Podręcznik programisty*.

### <a name="remarks"></a>Uwagi

Przydatne do pobierania właściwości z sesji.

## <a name="icommandimpl"></a> ICommandImpl::ICommandImpl

Konstruktor.

### <a name="syntax"></a>Składnia

```cpp
ICommandImpl();
```

## <a name="bcancel"></a> ICommandImpl::m_bCancel

Wskazuje, czy polecenie zostało anulowane.

### <a name="syntax"></a>Składnia

```cpp
unsigned m_bCancel:1;
```

### <a name="remarks"></a>Uwagi

Możesz pobrać tej zmiennej w `Execute` metody klasy poleceń i Anuluj zgodnie z potrzebami.

## <a name="bcancelwhenexecuting"></a> ICommandImpl::m_bCancelWhenExecuting

Wskazuje, czy polecenie może być anulowane podczas wykonywania.

### <a name="syntax"></a>Składnia

```cpp
unsigned m_bCancelWhenExecuting:1;
```

### <a name="remarks"></a>Uwagi

Wartość domyślna to **true** (może być anulowany,).

## <a name="bisexecuting"></a> ICommandImpl::m_bIsExecuting

Wskazuje, czy polecenie jest w trakcie wykonywania.

### <a name="syntax"></a>Składnia

```cpp
unsigned m_bIsExecuting:1;
```

### <a name="remarks"></a>Uwagi

`Execute` Metody klasy polecenia można ustawić tę zmienną **true**.

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)