---
title: Definicje typów ATL
ms.date: 11/04/2016
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
helpviewer_keywords:
- typedefs, ATL
- typedefs
- ATL, typedefs
ms.assetid: 7dd05baa-3efb-4e3b-af23-793c610f4560
ms.openlocfilehash: 5548bee36ac52dbd6add31241714b0404289be45
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319194"
---
# <a name="atl-typedefs"></a>Definicje typów ATL

Biblioteka aktywnych szablonów zawiera następujące typedefs.

|||
|-|-|
|[_ATL_BASE_MODULE](#_atl_base_module)|Zdefiniowany jako typedef na podstawie [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).|
|[_ATL_COM_MODULE](#_atl_com_module)|Zdefiniowany jako typedef na podstawie [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).|
|[_ATL_MODULE](#_atl_module)|Zdefiniowany jako typedef na podstawie [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).|
|[_ATL_WIN_MODULE](#_atl_win_module)|Zdefiniowana jako typedef na podstawie [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|
|[ATL_URL_PORT](#atl_url_port)|Typ używany przez [CUrl](../../atl/reference/curl-class.md) do określania numeru portu.|
|[CComDispatchDriver](#ccomdispatchdriver)|Ta klasa zarządza wskaźnikami interfejsu COM.|
|[Ccomglobalsthreadmodel](#ccomglobalsthreadmodel)|Wywołuje odpowiednie metody modelu wątku, niezależnie od modelu wątku używane.|
|[Ccomobjectthreadmodel](#ccomobjectthreadmodel)|Wywołuje odpowiednie metody modelu wątku, niezależnie od modelu wątku używane.|
|[CContainedWindow (Windows)](#ccontainedwindow)|Ta klasa jest specjalizacją `CContainedWindowT`.|
|[Ścieżka CPath](#cpath)|Specjalizacja [CPathT](../../atl/reference/cpatht-class.md) przy użyciu `CString`.|
|[CPathA (cpatha)](#cpatha)|Specjalizacja [CPathT](../../atl/reference/cpatht-class.md) przy użyciu `CStringA`.|
|[CPathW (Polski)](#cpathw)|Specjalizacja [CPathT](../../atl/reference/cpatht-class.md) przy użyciu `CStringW`.|
|[CSimpleValArray (Polski)](#csimplevalarray)|Reprezentuje tablicę do przechowywania typów prostych.|
|[DefaultThreadTraits (DefaultThreadTraits)](#defaultthreadtraits)|Klasa domyślnych cech wątku.|
|[LPCURL ( LPCURL )](#lpcurl)|Wskaźnik do stałego [obiektu CUrl.](../../atl/reference/curl-class.md)|
|[LPURL ( LPURL )](#lpurl)|Wskaźnik do obiektu [CUrl.](../../atl/reference/curl-class.md)|

## <a name="_atl_base_module"></a><a name="_atl_base_module"></a>_ATL_BASE_MODULE

Zdefiniowany jako typedef na podstawie _ATL_BASE_MODULE70.

```
typedef ATL::_ATL_BASE_MODULE70 _ATL_BASE_MODULE;
```

### <a name="remarks"></a>Uwagi

Używany w każdym projekcie ATL. Na podstawie [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).

Klasy, które są częścią ATL 7.0 Module Klasy pochodzą z _ATL_BASE_MODULE struktury.  Aby uzyskać więcej informacji na temat klas modułów ATL, zobacz [klasy modułów COM](../../atl/com-modules-classes.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcore.h

## <a name="_atl_com_module"></a><a name="_atl_com_module"></a>_ATL_COM_MODULE

Zdefiniowany jako typedef na podstawie _ATL_COM_MODULE70.

```
typedef ATL::_ATL_COM_MODULE70 _ATL_COM_MODULE;
```

### <a name="remarks"></a>Uwagi

Używane przez projekty ATL, które korzystają z funkcji COM. Na podstawie [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="_atl_module"></a><a name="_atl_module"></a>_ATL_MODULE

Zdefiniowany jako typedef na podstawie _ATL_MODULE70.

```
typedef ATL::_ATL_MODULE70 _ATL_MODULE;
```

## <a name="requirements"></a>Wymagania

**Nagłówka:**

### <a name="remarks"></a>Uwagi

Na podstawie [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).

## <a name="_atl_win_module"></a><a name="_atl_win_module"></a>_ATL_WIN_MODULE

Zdefiniowany jako typedef na podstawie _ATL_WIN_MODULE70.

```
typedef ATL::_ATL_WIN_MODULE70 _ATL_WIN_MODULE;
```

### <a name="remarks"></a>Uwagi

Używane przez wszystkie projekty ATL, które używają funkcji okien. Na podstawie [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="atl_url_port"></a><a name="atl_url_port"></a>ATL_URL_PORT

Typ używany przez [CUrl](curl-class.md) do określania numeru portu.

```
typedef WORD ATL_URL_PORT;
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlutil.h

## <a name="ccomdispatchdriver"></a><a name="ccomdispatchdriver"></a>CComDispatchDriver

Ta klasa zarządza wskaźnikami interfejsu COM.

```
typedef CComQIPtr<IDispatch, &__uuidof(IDispatch)> CComDispatchDriver;
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="ccomglobalsthreadmodel"></a><a name="ccomglobalsthreadmodel"></a>Ccomglobalsthreadmodel

Wywołuje odpowiednie metody modelu wątku, niezależnie od modelu wątku używane.

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

W zależności od modelu wątkowego używanego przez `CComGlobalsThreadModel` aplikację nazwa **typedef** odwołuje się do [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) lub [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Te klasy `typedef` zawierają dodatkowe nazwy, aby odwołać się do klasy sekcji krytycznej.

> [!NOTE]
> `CComGlobalsThreadModel`nie odwołuje się do klasy [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).

Korzystanie `CComGlobalsThreadModel` zwalnia z określania określonej klasy modelu wątku. Niezależnie od modelu wątkowego używane, odpowiednie metody zostaną wywołane.

Oprócz `CComGlobalsThreadModel`, ATL zawiera **nazwę typedef** [CComObjectThreadModel](#ccomobjectthreadmodel). Klasa, do którego `typedef` odwołuje się każda z nich, zależy od użytego modelu gwintowania, jak pokazano w poniższej tabeli:

| — klasa typedef|Pojedyncze gwintowanie|Gwintowanie mieszkań|Gwintowanie swobodne|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S= `CComSingleThreadModel`; M=`CComMultiThreadModel`

Użyj `CComObjectThreadModel` w ramach klasy jednego obiektu. Użyj `CComGlobalsThreadModel` w obiekcie, który jest globalnie dostępny dla programu lub gdy chcesz chronić zasoby modułu w wielu wątkach.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="ccomobjectthreadmodel"></a><a name="ccomobjectthreadmodel"></a>Ccomobjectthreadmodel

Wywołuje odpowiednie metody modelu wątku, niezależnie od modelu wątku używane.

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

W zależności od modelu `typedef` wątkowego używanego `CComObjectThreadModel` przez aplikację nazwa odwołuje się do [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) lub [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Te klasy `typedef` zawierają dodatkowe nazwy, aby odwołać się do klasy sekcji krytycznej.

> [!NOTE]
> `CComObjectThreadModel`nie odwołuje się do klasy [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).

Korzystanie `CComObjectThreadModel` zwalnia z określania określonej klasy modelu wątku. Niezależnie od modelu wątkowego używane, odpowiednie metody zostaną wywołane.

Oprócz `CComObjectThreadModel`, ATL zapewnia **nazwa typedef** [CComGlobalsThreadModel](#ccomglobalsthreadmodel). Klasa, do którego odwołuje się każdy **typedef,** zależy od użytego modelu gwintowania, jak pokazano w poniższej tabeli:

| — klasa typedef|Pojedyncze gwintowanie|Gwintowanie mieszkań|Gwintowanie swobodne|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S= `CComSingleThreadModel`; M=`CComMultiThreadModel`

Użyj `CComObjectThreadModel` w ramach klasy jednego obiektu. Użyj `CComGlobalsThreadModel` w obiekcie, który jest globalnie dostępny dla programu lub gdy chcesz chronić zasoby modułu w wielu wątkach.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="ccontainedwindow"></a><a name="ccontainedwindow"></a>CContainedWindow (Windows)

Ta klasa jest specjalizacją `CContainedWindowT`.

```
typedef CContainedWindowT<CWindow> CContainedWindow;
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

### <a name="remarks"></a>Uwagi

`CContainedWindow`jest specjalizacją [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md). Jeśli chcesz zmienić klasę podstawową lub `CContainedWindowT` cechy, użyj bezpośrednio.

## <a name="cpath"></a><a name="cpath"></a>Ścieżka CPath

Specjalizacja [CPathT](../../atl/reference/cpatht-class.md) przy użyciu `CString`.

```
typedef CPathT<CString> CPath;
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlpath.h

## <a name="cpatha"></a><a name="cpatha"></a>CPathA (cpatha)

Specjalizacja [CPathT](../../atl/reference/cpatht-class.md) przy użyciu `CStringA`.

```
typedef CPathT<CStringA> CPathA;
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlpath.h

## <a name="cpathw"></a><a name="cpathw"></a>CPathW (Polski)

Specjalizacja [CPathT](../../atl/reference/cpatht-class.md) przy użyciu `CStringW`.

```
typedef ATL::CPathT<CStringW> CPathW;
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlpath.h

## <a name="csimplevalarray"></a><a name="csimplevalarray"></a>CSimpleValArray (Polski)

Reprezentuje tablicę do przechowywania typów prostych.

```
#define CSimpleValArray CSimpleArray
```

### <a name="remarks"></a>Uwagi

`CSimpleValArray`jest przeznaczony do tworzenia tablic zawierających proste typy danych i zarządzania nimi. Jest to prosty #define [CSimpleArray](../../atl/reference/csimplearray-class.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsimpcoll.h

## <a name="lpcurl"></a><a name="lpcurl"></a>LPCURL ( LPCURL )

Wskaźnik do stałego [obiektu CUrl.](../../atl/reference/curl-class.md)

```
typedef const CUrl* LPCURL;
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlutil.h

## <a name="defaultthreadtraits"></a><a name="defaultthreadtraits"></a>DefaultThreadTraits (DefaultThreadTraits)

Klasa domyślnych cech wątku.

### <a name="syntax"></a>Składnia

```
#if defined(_MT)
   typedef CRTThreadTraits DefaultThreadTraits;
#else
   typedef Win32ThreadTraits DefaultThreadTraits;
#endif
```

## <a name="remarks"></a>Uwagi

Jeśli bieżący projekt używa wielowątkowego CRT, DefaultThreadTraits jest zdefiniowany jako CRTThreadTraits. W przeciwnym razie win32ThreadTraits jest używany.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="lpurl"></a><a name="lpurl"></a>LPURL ( LPURL )

Wskaźnik do obiektu [CUrl.](../../atl/reference/curl-class.md)

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
