---
title: Klasa CComAutoThreadModule
ms.date: 11/04/2016
f1_keywords:
- CComAutoThreadModule
- ATLBASE/ATL::CComAutoThreadModule
- ATLBASE/ATL::CreateInstance
- ATLBASE/ATL::GetDefaultThreads
- ATLBASE/ATL::Init
- ATLBASE/ATL::Lock
- ATLBASE/ATL::Unlock
- ATLBASE/ATL::dwThreadID
- ATLBASE/ATL::m_Allocator
- ATLBASE/ATL::m_nThreads
- ATLBASE/ATL::m_pApartments
helpviewer_keywords:
- CComAutoThreadModule class
- apartment model modules
ms.assetid: 13063ea5-a57e-4aac-97d3-227137262811
ms.openlocfilehash: 391354c5672cf15c0286491619a13c6005493cfa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321068"
---
# <a name="ccomautothreadmodule-class"></a>Klasa CComAutoThreadModule

Od ATL 7.0, `CComAutoThreadModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class ThreadAllocator = CComSimpleThreadAllocator>
class CComAutoThreadModule : public CComModule
```

#### <a name="parameters"></a>Parametry

*Lokalizator gwintów*<br/>
[w] Klasa zarządzająca wyborem wątku. Wartością domyślną jest [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[Createinstance](#createinstance)|Wybiera wątek, a następnie tworzy obiekt w skojarzonym mieszkaniu.|
|[GetDefaultWąs](#getdefaultthreads)|(Statyczne) Dynamicznie oblicza liczbę wątków dla modułu na podstawie liczby procesorów.|
|[Init](#init)|Tworzy wątki modułu.|
|[Blokady](#lock)|Zwiększa liczbę blokad na module i na bieżącym wątku.|
|[Odblokować](#unlock)|Zmniejsza liczbę blokad na module i na bieżącym wątku.|

### <a name="data-members"></a>Elementy członkowskie danych

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|[dwThreadID (Dw.](#dwthreadid)|Zawiera identyfikator bieżącego wątku.|
|[m_Allocator](#m_allocator)|Zarządza wyborem wątku.|
|[m_nThreads](#m_nthreads)|Zawiera liczbę wątków w module.|
|[m_pApartments](#m_papartments)|Zarządza mieszkaniami modułu.|

## <a name="remarks"></a>Uwagi

> [!NOTE]
> Ta klasa jest przestarzała, została zastąpiona przez [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) i [CAtlModule](../../atl/reference/catlmodule-class.md) klas pochodnych. Następujące informacje są przeznaczone do użytku ze starszymi wersjami atl.

`CComAutoThreadModule`pochodzi z [CComModule](../../atl/reference/ccommodule-class.md) do implementacji wątku puli, model apartamentu serwera COM dla EXEs i usług systemu Windows. `CComAutoThreadModule`używa [CComApartment](../../atl/reference/ccomapartment-class.md) do zarządzania mieszkaniem dla każdego wątku w module.

Wywiesić moduł z `CComAutoThreadModule` kiedy chcesz utworzyć obiekty w wielu mieszkaniach. Należy również dołączyć [makro DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) w definicji klasy obiektu, aby określić [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) jako fabrykę klas.

Domyślnie kreator aplikacji ATL COM AppWizard (Kreator projektu ATL w programie `CComModule`Visual Studio .NET) będzie czerpał z modułu . Aby `CComAutoThreadModule`użyć , zmodyfikuj definicję klasy. Przykład:

[!code-cpp[NVC_ATL_AxHost#2](../../atl/codesnippet/cpp/ccomautothreadmodule-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[Catlmodule](../../atl/reference/catlmodule-class.md)

`IAtlAutoThreadModule`

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)

[Ccommodule](../../atl/reference/ccommodule-class.md)

`CComAutoThreadModule`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="ccomautothreadmodulecreateinstance"></a><a name="createinstance"></a>CComAutoThreadModule::Tworzenie instance

Od ATL 7.0, `CComAutoThreadModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

```
HRESULT CreateInstance(
    void* pfnCreateInstance,
    REFIID riid,
    void** ppvObj);
```

### <a name="parameters"></a>Parametry

*pfnCreateInstance*<br/>
[w] Wskaźnik do funkcji twórcy.

*Riid*<br/>
[w] Identyfikator żądanego interfejsu.

*ppvObj (polski)*<br/>
[na zewnątrz] Wskaźnik do wskaźnika interfejsu identyfikowanego przez *riid*. Jeśli obiekt nie obsługuje tego interfejsu, *ppvObj* jest ustawiona na wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Wybiera wątek, a następnie tworzy obiekt w skojarzonym mieszkaniu.

## <a name="ccomautothreadmoduledwthreadid"></a><a name="dwthreadid"></a>CComAutoThreadModule::dwThreadID

Od ATL 7.0, `CComAutoThreadModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

```
DWORD dwThreadID;
```

### <a name="remarks"></a>Uwagi

Zawiera identyfikator bieżącego wątku.

## <a name="ccomautothreadmodulegetdefaultthreads"></a><a name="getdefaultthreads"></a>CComAutoThreadModule::GetDefaultWąs

Od ATL 7.0, `CComAutoThreadModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>Wartość zwracana

Liczba wątków, które mają zostać utworzone w module EXE.

### <a name="remarks"></a>Uwagi

Ta funkcja statyczna dynamicznie oblicza maksymalną liczbę wątków dla modułu EXE na podstawie liczby procesorów. Domyślnie ta zwracana wartość jest przekazywana do Metody [Init w](#init) celu utworzenia wątków.

## <a name="ccomautothreadmoduleinit"></a><a name="init"></a>CComAutoThreadModule::Init

Od ATL 7.0, `CComAutoThreadModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL,
    int nThreads = GetDefaultThreads());
```

### <a name="parameters"></a>Parametry

*P*<br/>
[w] Wskaźnik do tablicy wpisów mapy obiektów.

*H*<br/>
[w] HINSTANCE przeszedł `DLLMain` do `WinMain`lub .

*plibid ( plibid )*<br/>
[w] Wskaźnik do LIBID biblioteki typów skojarzonych z projektem.

*nWątki*<br/>
[w] Liczba wątków do utworzenia. Domyślnie *nNadanie* jest wartością zwróconą przez [GetDefaultThreads](#getdefaultthreads).

### <a name="remarks"></a>Uwagi

Inicjuje elementy członkowskie danych i tworzy liczbę wątków określonych przez *nThreads*.

## <a name="ccomautothreadmodulelock"></a><a name="lock"></a>CComAutoThreadModule::Lock

Od ATL 7.0, `CComAutoThreadModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

```
LONG Lock();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która może być przydatna do diagnostyki lub testowania.

### <a name="remarks"></a>Uwagi

Wykonuje przyrost atomowy na liczbie blokad dla modułu i dla bieżącego wątku. `CComAutoThreadModule`używa liczby blokad modułu, aby ustalić, czy klienci uzyskują dostęp do modułu. Liczba blokad dla bieżącego wątku jest używana do celów statystycznych.

## <a name="ccomautothreadmodulem_allocator"></a><a name="m_allocator"></a>CComAutoThreadModule::m_Allocator

Od ATL 7.0, `CComAutoThreadModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

```
ThreadAllocator  m_Allocator;
```

### <a name="remarks"></a>Uwagi

Obiekt zarządzający wyborem wątku. Domyślnie parametrem szablonu `ThreadAllocator` klasy jest [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

## <a name="ccomautothreadmodulem_nthreads"></a><a name="m_nthreads"></a>CComAutoThreadModule::m_nThreads

Od ATL 7.0, `CComAutoThreadModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

```
int m_nThreads;
```

### <a name="remarks"></a>Uwagi

Zawiera liczbę wątków w module EXE. Gdy wywoływana jest `m_nThreads` [init,](#init) jest ustawiona na wartość parametru *nThreads.* Każdy wątek skojarzony apartament jest zarządzany przez [CComApartment](../../atl/reference/ccomapartment-class.md) obiektu.

## <a name="ccomautothreadmodulem_papartments"></a><a name="m_papartments"></a>CComAutoThreadModule::m_pApartments

Od ATL 7.0, `CComAutoThreadModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

```
CComApartment* m_pApartments;
```

### <a name="remarks"></a>Uwagi

Wskazuje tablicę [CComApartment](../../atl/reference/ccomapartment-class.md) obiektów, z których każdy zarządza mieszkanie w module. Liczba elementów w tablicy jest oparta na [m_nThreads](#m_nthreads) element członkowski.

## <a name="ccomautothreadmoduleunlock"></a><a name="unlock"></a>CComAutoThreadModule::Odblokuj

Od ATL 7.0, `CComAutoThreadModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

```
LONG Unlock();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która może być przydatna do diagnostyki lub testowania.

### <a name="remarks"></a>Uwagi

Wykonuje atomowej dekrementacji na liczbę blokad dla modułu i dla bieżącego wątku. `CComAutoThreadModule`używa liczby blokad modułu, aby ustalić, czy klienci uzyskują dostęp do modułu. Liczba blokad dla bieżącego wątku jest używana do celów statystycznych.

Gdy liczba blokad modułu osiągnie zero, moduł może zostać zwolniony.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasy modułów](../../atl/atl-module-classes.md)
