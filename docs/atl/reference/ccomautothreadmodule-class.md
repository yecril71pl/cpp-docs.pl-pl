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
ms.openlocfilehash: 405b05548cda2b2d379b849d9278293b8d747d2e
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833793"
---
# <a name="ccomautothreadmodule-class"></a>Klasa CComAutoThreadModule

Począwszy od biblioteki ATL 7,0, `CComAutoThreadModule` jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class ThreadAllocator = CComSimpleThreadAllocator>
class CComAutoThreadModule : public CComModule
```

#### <a name="parameters"></a>Parametry

*ThreadAllocator*<br/>
podczas Klasa, która zarządza wyborem wątku. Wartość domyślna to [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|Funkcja|Opis|
|-|-|
|[CreateInstance](#createinstance)|Wybiera wątek, a następnie tworzy obiekt w skojarzonej tablicy.|
|[GetDefaultThreads](#getdefaultthreads)|Ruchom Dynamicznie oblicza liczbę wątków dla modułu na podstawie liczby procesorów.|
|[Init](#init)|Tworzy wątki modułu.|
|[Skręt](#lock)|Zwiększa liczbę blokad modułu i bieżącego wątku.|
|[Odblokowania](#unlock)|Zmniejsza liczbę blokad modułu i bieżącego wątku.|

### <a name="data-members"></a>Elementy członkowskie danych

|Element członkowski danych|Opis|
|-|-|
|[dwThreadID](#dwthreadid)|Zawiera identyfikator bieżącego wątku.|
|[m_Allocator](#m_allocator)|Zarządza wyborem wątku.|
|[m_nThreads](#m_nthreads)|Zawiera liczbę wątków w module.|
|[m_pApartments](#m_papartments)|Zarządza apartamentach modułu.|

## <a name="remarks"></a>Uwagi

> [!NOTE]
> Ta klasa jest przestarzała, która została zastąpiona przez klasy pochodne [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) i [CAtlModule](../../atl/reference/catlmodule-class.md) . Poniższe informacje są przeznaczone do użycia ze starszymi wersjami ATL.

`CComAutoThreadModule` wynika z [CComModule](../../atl/reference/ccommodule-class.md) , aby ZAIMPLEMENTOWAĆ serwer com z pulą wątków, który jest modelem typu Apartment dla exe i usług systemu Windows. `CComAutoThreadModule` używa [CComApartment](../../atl/reference/ccomapartment-class.md) do zarządzania komórką dla każdego wątku w module.

Wykorzystaj moduł od `CComAutoThreadModule` momentu, gdy chcesz tworzyć obiekty w wielu apartamentach. Należy również uwzględnić makro [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) w definicji klasy obiektu, aby określić [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) jako fabrykę klas.

Domyślnie ATL COM AppWizard (Kreator projektu ATL w Visual Studio .NET) będzie pochodzić z modułu `CComModule` . Aby użyć `CComAutoThreadModule` , należy zmodyfikować definicję klasy. Na przykład:

[!code-cpp[NVC_ATL_AxHost#2](../../atl/codesnippet/cpp/ccomautothreadmodule-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

`IAtlAutoThreadModule`

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)

[CComModule](../../atl/reference/ccommodule-class.md)

`CComAutoThreadModule`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

## <a name="ccomautothreadmodulecreateinstance"></a><a name="createinstance"></a> CComAutoThreadModule:: CreateInstance

Począwszy od biblioteki ATL 7,0, `CComAutoThreadModule` jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
HRESULT CreateInstance(
    void* pfnCreateInstance,
    REFIID riid,
    void** ppvObj);
```

### <a name="parameters"></a>Parametry

*pfnCreateInstance*<br/>
podczas Wskaźnik do funkcji Creator.

*riid*<br/>
podczas Identyfikator IID żądanego interfejsu.

*ppvObj*<br/>
określoną Wskaźnik do wskaźnika interfejsu identyfikowanego przez *riid*. Jeśli obiekt nie obsługuje tego interfejsu, *ppvObj* ma wartość null.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Wybiera wątek, a następnie tworzy obiekt w skojarzonej tablicy.

## <a name="ccomautothreadmoduledwthreadid"></a><a name="dwthreadid"></a> CComAutoThreadModule::d wThreadID

Począwszy od biblioteki ATL 7,0, `CComAutoThreadModule` jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
DWORD dwThreadID;
```

### <a name="remarks"></a>Uwagi

Zawiera identyfikator bieżącego wątku.

## <a name="ccomautothreadmodulegetdefaultthreads"></a><a name="getdefaultthreads"></a> CComAutoThreadModule::GetDefaultThreads

Począwszy od biblioteki ATL 7,0, `CComAutoThreadModule` jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>Wartość zwracana

Liczba wątków, które mają zostać utworzone w module EXE.

### <a name="remarks"></a>Uwagi

Ta funkcja statyczna dynamicznie oblicza maksymalną liczbę wątków dla modułu EXE na podstawie liczby procesorów. Domyślnie ta wartość zwracana jest przesyłana do metody [init](#init) w celu utworzenia wątków.

## <a name="ccomautothreadmoduleinit"></a><a name="init"></a> CComAutoThreadModule:: init

Począwszy od biblioteki ATL 7,0, `CComAutoThreadModule` jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL,
    int nThreads = GetDefaultThreads());
```

### <a name="parameters"></a>Parametry

*St*<br/>
podczas Wskaźnik do tablicy wpisów mapy obiektu.

*c*<br/>
podczas HINSTANCE przeszedł do `DLLMain` lub `WinMain` .

*plibid*<br/>
podczas Wskaźnik do identyfikatora LIBID biblioteki typów skojarzonej z projektem.

*nThreads*<br/>
podczas Liczba wątków, które mają zostać utworzone. Domyślnie *nThreads* jest wartością zwracaną przez [GetDefaultThreads](#getdefaultthreads).

### <a name="remarks"></a>Uwagi

Inicjuje składowe danych i tworzy liczbę wątków określoną przez *nThreads*.

## <a name="ccomautothreadmodulelock"></a><a name="lock"></a> CComAutoThreadModule:: Lock

Począwszy od biblioteki ATL 7,0, `CComAutoThreadModule` jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
LONG Lock();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która może być przydatna w przypadku diagnostyki lub testowania.

### <a name="remarks"></a>Uwagi

Wykonuje niepodzielny przyrost liczby blokad dla modułu i dla bieżącego wątku. `CComAutoThreadModule` używa liczby blokad modułu do określenia, czy wszyscy klienci uzyskują dostęp do modułu. Liczba blokad w bieżącym wątku jest używana do celów statystycznych.

## <a name="ccomautothreadmodulem_allocator"></a><a name="m_allocator"></a> CComAutoThreadModule:: m_Allocator

Począwszy od biblioteki ATL 7,0, `CComAutoThreadModule` jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
ThreadAllocator  m_Allocator;
```

### <a name="remarks"></a>Uwagi

Obiekt, który zarządza wybieraniem wątków. Domyślnie `ThreadAllocator` parametr szablonu klasy to [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

## <a name="ccomautothreadmodulem_nthreads"></a><a name="m_nthreads"></a> CComAutoThreadModule:: m_nThreads

Począwszy od biblioteki ATL 7,0, `CComAutoThreadModule` jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
int m_nThreads;
```

### <a name="remarks"></a>Uwagi

Zawiera liczbę wątków w module EXE. Gdy jest wywoływana [Inicjalizacja](#init) , `m_nThreads` jest ustawiona na wartość parametru *nThreads* . Komórka skojarzona z każdym wątkiem jest zarządzana przez obiekt [CComApartment](../../atl/reference/ccomapartment-class.md) .

## <a name="ccomautothreadmodulem_papartments"></a><a name="m_papartments"></a> CComAutoThreadModule:: m_pApartments

Począwszy od biblioteki ATL 7,0, `CComAutoThreadModule` jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
CComApartment* m_pApartments;
```

### <a name="remarks"></a>Uwagi

Wskazuje tablicę obiektów [CComApartment](../../atl/reference/ccomapartment-class.md) , z których każdy zarządza Apartament w module. Liczba elementów w tablicy jest oparta na elemencie członkowskim [m_nThreads](#m_nthreads) .

## <a name="ccomautothreadmoduleunlock"></a><a name="unlock"></a> CComAutoThreadModule:: Unlock

Począwszy od biblioteki ATL 7,0, `CComAutoThreadModule` jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
LONG Unlock();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która może być przydatna w przypadku diagnostyki lub testowania.

### <a name="remarks"></a>Uwagi

Wykonuje niepodzielną liczbę blokad dla modułu i dla bieżącego wątku. `CComAutoThreadModule` używa liczby blokad modułu do określenia, czy wszyscy klienci uzyskują dostęp do modułu. Liczba blokad w bieżącym wątku jest używana do celów statystycznych.

Gdy liczba blokad modułu osiągnie zero, moduł może zostać zwolniony.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasy modułów](../../atl/atl-module-classes.md)
