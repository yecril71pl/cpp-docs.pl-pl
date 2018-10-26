---
title: Definicje typów ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcore/ATL::_ATL_BASE_MODULE
- atlbase/ATL::_ATL_COM_MODULE
- atlbase/ATL::_ATL_MODULE
- atlbase/ATL::_ATL_WIN_MODULE
- atlutil/ATL::ATL_URL_PORT
- atlbase/ATL::CComDispatchDriver
- atlbase/ATL::CComGlobalsThreadModel
- atlbase/ATL::CComObjectThreadModel
- atlwin/ATL::CContainedWindow
- atlpath/ATL::CPath
- atlpath/ATL::CPathA
- atlpath/ATL::CPathW
- " atlsimpcoll/ATL::CSimpleValArray"
- " atlutil/ATL::LPCURL"
- atlbase/ATL::DefaultThreadTraits
- atlutil/ATL::LPURL
dev_langs:
- C++
helpviewer_keywords:
- typedefs, ATL
- typedefs
- ATL, typedefs
ms.assetid: 7dd05baa-3efb-4e3b-af23-793c610f4560
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9835b8cadb5a24aea130b1e32d919ebb49d20293
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065699"
---
# <a name="atl-typedefs"></a>Definicje typów ATL

Biblioteki Active Template Library zawiera poniższe definicje typów.

|||
|-|-|
|[_ATL_BASE_MODULE](#_atl_base_module)|Zdefiniowane jako element typedef, w oparciu o [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).|
|[_ATL_COM_MODULE](#_atl_com_module)|Zdefiniowane jako element typedef, w oparciu o [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).|
|[_ATL_MODULE](#_atl_module)|Zdefiniowane jako element typedef, w oparciu o [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).|
|[_ATL_WIN_MODULE](#_atl_win_module)|Zdefiniowane jako element typedef, w oparciu o [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|
|[ATL_URL_PORT](#atl_url_port)|Typ używany przez [CUrl](../../atl/reference/curl-class.md) do określania numeru portu.|
|[CComDispatchDriver](#ccomdispatchdriver)|Ta klasa zarządza wskaźniki interfejsu COM.|
|[CComGlobalsThreadModel](#ccomglobalsthreadmodel)|Wywołuje odpowiedniego wątku metody modelu, niezależnie od tego modelu wątkowości używane.|
|[CComObjectThreadModel](#ccomobjectthreadmodel)|Wywołuje odpowiedniego wątku metody modelu, niezależnie od tego modelu wątkowości używane.|
|[CContainedWindow](#ccontainedwindow)|Ta klasa jest specjalizacją `CContainedWindowT`.|
|[CPath](#cpath)|Specjalizacja [CPathT](../../atl/reference/cpatht-class.md) przy użyciu `CString`.|
|[CPathA](#cpatha)|Specjalizacja [CPathT](../../atl/reference/cpatht-class.md) przy użyciu `CStringA`.|
|[CPathW](#cpathw)|Specjalizacja [CPathT](../../atl/reference/cpatht-class.md) przy użyciu `CStringW`.|
|[CSimpleValArray](#csimplevalarray)|Reprezentuje tablicę do przechowywania typów prostych.|
|[DefaultThreadTraits](#defaultthreadtraits)|Domyślna klasa cech wątku.|
|[LPCURL](#lpcurl)|Wskaźnik na stałą [CUrl](../../atl/reference/curl-class.md) obiektu.|
|[LPURL](#lpurl)|Wskaźnik do [CUrl](../../atl/reference/curl-class.md) obiektu.|

##  <a name="_atl_base_module"></a>  _ATL_BASE_MODULE

Zdefiniowany jako element typedef, w oparciu o _ATL_BASE_MODULE70.

```
typedef ATL::_ATL_BASE_MODULE70 _ATL_BASE_MODULE;
```

### <a name="remarks"></a>Uwagi

Używany w każdym projekcie ATL. Na podstawie [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).

Klasy, które są częścią klasy modułów ATL 7.0 pochodzi od struktury _ATL_BASE_MODULE.  Aby uzyskać więcej informacji na temat klasy modułów ATL, zobacz [klasy modułów COM](../../atl/com-modules-classes.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcore.h

##  <a name="_atl_com_module"></a>  _ATL_COM_MODULE

Zdefiniowany jako element typedef, w oparciu o _ATL_COM_MODULE70.

```
typedef ATL::_ATL_COM_MODULE70 _ATL_COM_MODULE;
```

### <a name="remarks"></a>Uwagi

Używane w projektach ATL, korzystające z funkcji COM. Na podstawie [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="_atl_module"></a>  _ATL_MODULE

Zdefiniowany jako element typedef, w oparciu o _ATL_MODULE70.

```
typedef ATL::_ATL_MODULE70 _ATL_MODULE;
```

## <a name="requirements"></a>Wymagania

**Nagłówek:**

### <a name="remarks"></a>Uwagi

Na podstawie [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).

##  <a name="_atl_win_module"></a>  _ATL_WIN_MODULE

Zdefiniowany jako element typedef, w oparciu o _ATL_WIN_MODULE70.

```
typedef ATL::_ATL_WIN_MODULE70 _ATL_WIN_MODULE;
```

### <a name="remarks"></a>Uwagi

Używany przez wszystkie projekty biblioteki ATL, korzystające z funkcji obsługi okien. Na podstawie [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="atl_url_port"></a>  ATL_URL_PORT

Typ używany przez [CUrl](curl-class.md) do określania numeru portu.

```
typedef WORD ATL_URL_PORT;
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlutil.h

##  <a name="ccomdispatchdriver"></a>  CComDispatchDriver

Ta klasa zarządza wskaźniki interfejsu COM.

```
typedef CComQIPtr<IDispatch, &__uuidof(IDispatch)> CComDispatchDriver;
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="ccomglobalsthreadmodel"></a>  CComGlobalsThreadModel

Wywołuje odpowiedniego wątku metody modelu, niezależnie od tego modelu wątkowości używane.

```
#if defined(_ATL_SINGLE_THREADED)
typedef CComSingleThreadModel CComGlobalsThreadModel;
#elif defined(_ATL_APARTMENT_THREADED)
typedef CComMultiThreadModel CComGlobalsThreadModel;
#elif defined(_ATL_FREE_THREADED)
typedef CComMultiThreadModel CComGlobalsThreadModel;
#else
#pragma message ("No global threading model defined")
#endif
```

### <a name="remarks"></a>Uwagi

W zależności od modelu wątkowości używanych przez aplikację **typedef** nazwa `CComGlobalsThreadModel` odwołuje się do albo [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) lub [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Te klasy oferują dodatkowe `typedef` nazwy, aby odwoływać się do klasy sekcji krytycznych.

> [!NOTE]
> `CComGlobalsThreadModel` nie odwołuje się do klasy [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).

Za pomocą `CComGlobalsThreadModel` uwalnia użytkownika od określenia konkretnej klasy modelu wątkowości. Niezależnie od tego modelu wątkowości używany zostanie wywołana właściwe metody.

Oprócz `CComGlobalsThreadModel`, ATL dostarcza **typedef** nazwa [CComObjectThreadModel](#ccomobjectthreadmodel). Klasa przywoływana przez każdą `typedef` zależy od modelu wątkowości używane, jak pokazano w poniższej tabeli:

|— klasa typedef|Pojedynczy wątkowości|Wątkowość|Bezpłatne wątkowości|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`; M = `CComMultiThreadModel`

Użyj `CComObjectThreadModel` w ramach pojedynczego obiektu klasy. Użyj `CComGlobalsThreadModel` w obiekcie dostępnej globalnie do programu, lub gdy zachodzi potrzeba ochrony zasobów modułu w wielu wątkach.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="ccomobjectthreadmodel"></a>  CComObjectThreadModel

Wywołuje odpowiedniego wątku metody modelu, niezależnie od tego modelu wątkowości używane.

```
#if defined(_ATL_SINGLE_THREADED)
typedef CComSingleThreadModel CComObjectThreadModel;
#elif defined(_ATL_APARTMENT_THREADED)
typedef CComSingleThreadModel CComObjectThreadModel;
#elif defined(_ATL_FREE_THREADED)
typedef CComMultiThreadModel CComObjectThreadModel;
#else
#pragma message ("No global threading model defined")
#endif
```

### <a name="remarks"></a>Uwagi

W zależności od modelu wątkowości używanych przez aplikację `typedef` nazwa `CComObjectThreadModel` odwołuje się do albo [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) lub [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Te klasy oferują dodatkowe `typedef` nazwy, aby odwoływać się do klasy sekcji krytycznych.

> [!NOTE]
> `CComObjectThreadModel` nie odwołuje się do klasy [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).

Za pomocą `CComObjectThreadModel` uwalnia użytkownika od określenia konkretnej klasy modelu wątkowości. Niezależnie od tego modelu wątkowości używany zostanie wywołana właściwe metody.

Oprócz `CComObjectThreadModel`, ATL dostarcza **typedef** nazwa [CComGlobalsThreadModel](#ccomglobalsthreadmodel). Klasa przywoływana przez każdą **typedef** zależy od modelu wątkowości używane, jak pokazano w poniższej tabeli:

|— klasa typedef|Pojedynczy wątkowości|Wątkowość|Bezpłatne wątkowości|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`; M = `CComMultiThreadModel`

Użyj `CComObjectThreadModel` w ramach pojedynczego obiektu klasy. Użyj `CComGlobalsThreadModel` w obiekcie, który jest ogólnie dostępna, do programu lub jeśli chcesz chronić zasoby modułu w wielu wątkach.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="ccontainedwindow"></a>  CContainedWindow

Ta klasa jest specjalizacją `CContainedWindowT`.

```
typedef CContainedWindowT<CWindow> CContainedWindow;
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

### <a name="remarks"></a>Uwagi

`CContainedWindow` jest specjalizacją [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md). Jeśli chcesz zmienić cechy lub klasy bazowej, użyj `CContainedWindowT` bezpośrednio.

##  <a name="cpath"></a>  CPath

Specjalizacja [CPathT](../../atl/reference/cpatht-class.md) przy użyciu `CString`.

```
typedef CPathT<CString> CPath;
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlpath.h

##  <a name="cpatha"></a>  CPathA

Specjalizacja [CPathT](../../atl/reference/cpatht-class.md) przy użyciu `CStringA`.

```
typedef CPathT<CStringA> CPathA;
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlpath.h

##  <a name="cpathw"></a>  CPathW

Specjalizacja [CPathT](../../atl/reference/cpatht-class.md) przy użyciu `CStringW`.

```
typedef ATL::CPathT<CStringW> CPathW;
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlpath.h

##  <a name="csimplevalarray"></a>  CSimpleValArray

Reprezentuje tablicę do przechowywania typów prostych.

```
#define CSimpleValArray CSimpleArray
```

### <a name="remarks"></a>Uwagi

`CSimpleValArray` jest dostępna do tworzenia i zarządzania nimi w tablicach zawierających typy proste dane. Jest to prosty #define z [CSimpleArray](../../atl/reference/csimplearray-class.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsimpcoll.h

##  <a name="lpcurl"></a>  LPCURL

Wskaźnik na stałą [CUrl](../../atl/reference/curl-class.md) obiektu.

```
typedef const CUrl* LPCURL;
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlutil.h

##  <a name="defaultthreadtraits"></a>  DefaultThreadTraits

Domyślna klasa cech wątku.

### <a name="syntax"></a>Składnia

```
#if defined(_MT)
   typedef CRTThreadTraits DefaultThreadTraits;
#else
   typedef Win32ThreadTraits DefaultThreadTraits;
#endif
```

## <a name="remarks"></a>Uwagi

Jeśli bieżący projekt używa wielowątkowe CRT, DefaultThreadTraits jest zdefiniowany jako CRTThreadTraits. W przeciwnym razie Win32ThreadTraits jest używany.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="lpurl"></a>  LPURL

Wskaźnik do [CUrl](../../atl/reference/curl-class.md) obiektu.

```
typedef CUrl* LPURL;
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlutil.h

## <a name="see-also"></a>Zobacz też

[Składniki ATL COM pulpitu](../../atl/atl-com-desktop-components.md)<br/>
[Funkcje](../../atl/reference/atl-functions.md)<br/>
[Zmienne globalne](../../atl/reference/atl-global-variables.md)<br/>
[Klasy i struktury](../../atl/reference/atl-classes.md)<br/>
[Makra](../../atl/reference/atl-macros.md)
