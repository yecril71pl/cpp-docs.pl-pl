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
ms.openlocfilehash: 9b0fa685bf9a7de94b158bd62b00161c1b58562d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866176"
---
# <a name="ccomautothreadmodule-class"></a>Klasa CComAutoThreadModule

Od biblioteki ATL 7,0 `CComAutoThreadModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

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

|||
|-|-|
|[CreateInstance](#createinstance)|Wybiera wątek, a następnie tworzy obiekt w skojarzonej tablicy.|
|[GetDefaultThreads](#getdefaultthreads)|Ruchom Dynamicznie oblicza liczbę wątków dla modułu na podstawie liczby procesorów.|
|[Init](#init)|Tworzy wątki modułu.|
|[Skręt](#lock)|Zwiększa liczbę blokad modułu i bieżącego wątku.|
|[Odblokowania](#unlock)|Zmniejsza liczbę blokad modułu i bieżącego wątku.|

### <a name="data-members"></a>Elementy członkowskie danych

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|[dwThreadID](#dwthreadid)|Zawiera identyfikator bieżącego wątku.|
|[m_Allocator](#m_allocator)|Zarządza wyborem wątku.|
|[m_nThreads](#m_nthreads)|Zawiera liczbę wątków w module.|
|[m_pApartments](#m_papartments)|Zarządza apartamentach modułu.|

## <a name="remarks"></a>Uwagi

> [!NOTE]
>  Ta klasa jest przestarzała, która została zastąpiona przez klasy pochodne [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) i [CAtlModule](../../atl/reference/catlmodule-class.md) . Poniższe informacje są przeznaczone do użycia ze starszymi wersjami ATL.

`CComAutoThreadModule` wynika z [CComModule](../../atl/reference/ccommodule-class.md) , aby ZAIMPLEMENTOWAĆ serwer com z pulą wątków, który jest modelem typu Apartment dla exe i usług systemu Windows. `CComAutoThreadModule` używa [CComApartment](../../atl/reference/ccomapartment-class.md) do zarządzania komórką dla każdego wątku w module.

Wykorzystaj moduł z `CComAutoThreadModule`, gdy chcesz utworzyć obiekty w wielu apartamentach. Należy również uwzględnić makro [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) w definicji klasy obiektu, aby określić [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) jako fabrykę klas.

Domyślnie ATL COM AppWizard (Kreator projektu ATL w Visual Studio .NET) będzie dziedziczyć moduł od `CComModule`. Aby użyć `CComAutoThreadModule`, zmodyfikuj definicję klasy. Na przykład:

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

##  <a name="createinstance"></a>CComAutoThreadModule:: CreateInstance

Od biblioteki ATL 7,0 `CComAutoThreadModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

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

##  <a name="dwthreadid"></a>CComAutoThreadModule::d wThreadID

Od biblioteki ATL 7,0 `CComAutoThreadModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
DWORD dwThreadID;
```

### <a name="remarks"></a>Uwagi

Zawiera identyfikator bieżącego wątku.

##  <a name="getdefaultthreads"></a>CComAutoThreadModule::GetDefaultThreads

Od biblioteki ATL 7,0 `CComAutoThreadModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>Wartość zwracana

Liczba wątków, które mają zostać utworzone w module EXE.

### <a name="remarks"></a>Uwagi

Ta funkcja statyczna dynamicznie oblicza maksymalną liczbę wątków dla modułu EXE na podstawie liczby procesorów. Domyślnie ta wartość zwracana jest przesyłana do metody [init](#init) w celu utworzenia wątków.

##  <a name="init"></a>CComAutoThreadModule:: init

Od biblioteki ATL 7,0 `CComAutoThreadModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

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
podczas HINSTANCE przeszedł do `DLLMain` lub `WinMain`.

*plibid*<br/>
podczas Wskaźnik do identyfikatora LIBID biblioteki typów skojarzonej z projektem.

*nThreads*<br/>
podczas Liczba wątków, które mają zostać utworzone. Domyślnie *nThreads* jest wartością zwracaną przez [GetDefaultThreads](#getdefaultthreads).

### <a name="remarks"></a>Uwagi

Inicjuje składowe danych i tworzy liczbę wątków określoną przez *nThreads*.

##  <a name="lock"></a>CComAutoThreadModule:: Lock

Od biblioteki ATL 7,0 `CComAutoThreadModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
LONG Lock();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która może być przydatna w przypadku diagnostyki lub testowania.

### <a name="remarks"></a>Uwagi

Wykonuje niepodzielny przyrost liczby blokad dla modułu i dla bieżącego wątku. `CComAutoThreadModule` używa liczby blokad modułu, aby określić, czy wszyscy klienci uzyskują dostęp do modułu. Liczba blokad w bieżącym wątku jest używana do celów statystycznych.

##  <a name="m_allocator"></a>CComAutoThreadModule:: m_Allocator

Od biblioteki ATL 7,0 `CComAutoThreadModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
ThreadAllocator  m_Allocator;
```

### <a name="remarks"></a>Uwagi

Obiekt, który zarządza wybieraniem wątków. Domyślnie parametr szablonu klasy `ThreadAllocator` to [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

##  <a name="m_nthreads"></a>CComAutoThreadModule:: m_nThreads

Od biblioteki ATL 7,0 `CComAutoThreadModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
int m_nThreads;
```

### <a name="remarks"></a>Uwagi

Zawiera liczbę wątków w module EXE. Gdy jest wywoływana [Inicjalizacja](#init) , `m_nThreads` jest ustawiona na wartość parametru *nThreads* . Komórka skojarzona z każdym wątkiem jest zarządzana przez obiekt [CComApartment](../../atl/reference/ccomapartment-class.md) .

##  <a name="m_papartments"></a>CComAutoThreadModule:: m_pApartments

Od biblioteki ATL 7,0 `CComAutoThreadModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
CComApartment* m_pApartments;
```

### <a name="remarks"></a>Uwagi

Wskazuje tablicę obiektów [CComApartment](../../atl/reference/ccomapartment-class.md) , z których każdy zarządza Apartament w module. Liczba elementów w tablicy jest oparta na elemencie członkowskim [m_nThreads](#m_nthreads) .

##  <a name="unlock"></a>CComAutoThreadModule:: Unlock

Od biblioteki ATL 7,0 `CComAutoThreadModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
LONG Unlock();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która może być przydatna w przypadku diagnostyki lub testowania.

### <a name="remarks"></a>Uwagi

Wykonuje niepodzielną liczbę blokad dla modułu i dla bieżącego wątku. `CComAutoThreadModule` używa liczby blokad modułu, aby określić, czy wszyscy klienci uzyskują dostęp do modułu. Liczba blokad w bieżącym wątku jest używana do celów statystycznych.

Gdy liczba blokad modułu osiągnie zero, moduł może zostać zwolniony.

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasy modułów](../../atl/atl-module-classes.md)
