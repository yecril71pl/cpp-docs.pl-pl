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
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271999"
---
# <a name="ccomautothreadmodule-class"></a>Klasa CComAutoThreadModule

Począwszy od ATL 7.0 `CComAutoThreadModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template <class ThreadAllocator = CComSimpleThreadAllocator>
class CComAutoThreadModule : public CComModule
```

#### <a name="parameters"></a>Parametry

*ThreadAllocator*<br/>
[in] Klasa zarządzania wybór wątku. Wartość domyślna to [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[CreateInstance](#createinstance)|Wybiera wątku, a następnie tworzy obiekt w apartamentu skojarzone.|
|[GetDefaultThreads](#getdefaultthreads)|(Statyczny) Dynamicznie oblicza liczbę wątków dla modułu na podstawie liczby procesorów.|
|[Init](#init)|Tworzy moduł wątków.|
|[Blokady](#lock)|Zwiększa liczbę blokad modułu i w bieżącym wątku.|
|[Unlock](#unlock)|Zmniejsza liczbę blokad modułu i w bieżącym wątku.|

### <a name="data-members"></a>Elementy członkowskie danych

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|[dwThreadID](#dwthreadid)|Zawiera identyfikator bieżącego wątku.|
|[m_Allocator](#m_allocator)|Zarządza wybór wątku.|
|[m_nThreads](#m_nthreads)|Zawiera liczbę wątków w module.|
|[m_pApartments](#m_papartments)|Zarządza apartamentach modułu.|

## <a name="remarks"></a>Uwagi

> [!NOTE]
>  Ta klasa jest przestarzały, zastąpione przez [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) i [CAtlModule](../../atl/reference/catlmodule-class.md) klas pochodnych. Informacje, który następuje po jest przeznaczony dla starszej wersji ATL.

`CComAutoThreadModule` pochodzi od klasy [CComModule](../../atl/reference/ccommodule-class.md) do wdrożenia serwera wątków w puli, model przedziału COM dla usług plików exe i Windows. `CComAutoThreadModule` używa [CComApartment](../../atl/reference/ccomapartment-class.md) Zarządzanie apartament dla każdego wątku w module.

Pochodzi z modułu `CComAutoThreadModule` gdy zachodzi potrzeba tworzenia obiektów w wielu apartamentach. Należy również uwzględnić [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) makra w definicji klasy do obiektu, aby określić [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) jako fabryki klas.

Domyślnie przez AppWizard COM ATL (ATL Kreator projektu w programie Visual Studio .NET), z której pochodzą z modułu `CComModule`. Aby użyć `CComAutoThreadModule`, należy zmodyfikować definicję klasy. Na przykład:

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

**Nagłówek:** atlbase.h

##  <a name="createinstance"></a>  CComAutoThreadModule::CreateInstance

Począwszy od ATL 7.0 `CComAutoThreadModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

```
HRESULT CreateInstance(
    void* pfnCreateInstance,
    REFIID riid,
    void** ppvObj);
```

### <a name="parameters"></a>Parametry

*pfnCreateInstance*<br/>
[in] Wskaźnik do funkcji twórcy.

*Parametr riid*<br/>
[in] Identyfikator IID żądanego interfejsu.

*ppvObj*<br/>
[out] Wskaźnik do wskaźnika interfejsu identyfikowane przez *riid*. Jeśli obiekt nie obsługuje ten interfejs *ppvObj* ma wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Wybiera wątku, a następnie tworzy obiekt w apartamentu skojarzone.

##  <a name="dwthreadid"></a>  CComAutoThreadModule::dwThreadID

Począwszy od ATL 7.0 `CComAutoThreadModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

```
DWORD dwThreadID;
```

### <a name="remarks"></a>Uwagi

Zawiera identyfikator bieżącego wątku.

##  <a name="getdefaultthreads"></a>  CComAutoThreadModule::GetDefaultThreads

Począwszy od ATL 7.0 `CComAutoThreadModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>Wartość zwracana

Liczba wątków, które zostały utworzone w EXE module.

### <a name="remarks"></a>Uwagi

Ta funkcja statyczna dynamicznie oblicza maksymalną liczbę wątków dla modułu "EXE", na podstawie liczby procesorów. Domyślnie ta wartość zwracana jest przekazywany do [Init](#init) metodą tworzenia wątków.

##  <a name="init"></a>  CComAutoThreadModule::Init

Począwszy od ATL 7.0 `CComAutoThreadModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL,
    int nThreads = GetDefaultThreads());
```

### <a name="parameters"></a>Parametry

*p*<br/>
[in] Wskaźnik do tablicy obiektu wpisy mapy.

*h*<br/>
[in] HINSTANCE przekazany do `DLLMain` lub `WinMain`.

*plibid*<br/>
[in] Wskaźnik do identyfikatora LIBID biblioteki typów, skojarzone z tym projektem.

*nThreads*<br/>
[in] Liczba wątków, które ma zostać utworzony. Domyślnie *nThreads* jest wartość zwrócona przez obiekt [GetDefaultThreads](#getdefaultthreads).

### <a name="remarks"></a>Uwagi

Inicjuje elementy członkowskie danych i tworzy liczbę wątków, określony przez *nThreads*.

##  <a name="lock"></a>  CComAutoThreadModule::Lock

Począwszy od ATL 7.0 `CComAutoThreadModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

```
LONG Lock();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która może być użyteczna, diagnostykę lub testowania.

### <a name="remarks"></a>Uwagi

Wykonuje niepodzielne zwiększając liczbę blokad modułu i dla bieżącego wątku. `CComAutoThreadModule` używa liczbę blokad modułu, aby określić, czy wszyscy klienci uzyskują dostęp do modułu. Liczba blokad dla bieżącego wątku jest używana do celów statystycznych.

##  <a name="m_allocator"></a>  CComAutoThreadModule::m_Allocator

Począwszy od ATL 7.0 `CComAutoThreadModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

```
ThreadAllocator  m_Allocator;
```

### <a name="remarks"></a>Uwagi

Obiekt zarządzania wybór wątku. Domyślnie `ThreadAllocator` parametr szablonu klasy jest [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

##  <a name="m_nthreads"></a>  CComAutoThreadModule::m_nThreads

Począwszy od ATL 7.0 `CComAutoThreadModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

```
int m_nThreads;
```

### <a name="remarks"></a>Uwagi

Zawiera liczbę wątków w EXE module. Gdy [Init](#init) jest wywoływana, `m_nThreads` ustawiono *nThreads* wartość parametru. Skojarzone apartamentu każdy wątek jest zarządzana przez [CComApartment](../../atl/reference/ccomapartment-class.md) obiektu.

##  <a name="m_papartments"></a>  CComAutoThreadModule::m_pApartments

Począwszy od ATL 7.0 `CComAutoThreadModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

```
CComApartment* m_pApartments;
```

### <a name="remarks"></a>Uwagi

Wskazuje na tablicę [CComApartment](../../atl/reference/ccomapartment-class.md) obiektów, z których każdy zarządza typu apartment w module. Liczba elementów w tablicy opiera się na [m_nThreads](#m_nthreads) elementu członkowskiego.

##  <a name="unlock"></a>  CComAutoThreadModule::Unlock

Począwszy od ATL 7.0 `CComAutoThreadModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

```
LONG Unlock();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która może być użyteczna, diagnostykę lub testowania.

### <a name="remarks"></a>Uwagi

Wykonuje niepodzielne dekrementacji na liczbę blokad modułu i dla bieżącego wątku. `CComAutoThreadModule` używa liczbę blokad modułu, aby określić, czy wszyscy klienci uzyskują dostęp do modułu. Liczba blokad dla bieżącego wątku jest używana do celów statystycznych.

Gdy liczbę blokad modułu osiągnie zero, moduł może być zwolniony.

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../../atl/atl-class-overview.md)<br/>
[Klasy modułów](../../atl/atl-module-classes.md)
