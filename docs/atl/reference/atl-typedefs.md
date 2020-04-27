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
ms.openlocfilehash: 26e4e80ed3110351130731e6030427d25fc4a0ea
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168738"
---
# <a name="atl-typedefs"></a>Definicje typów ATL

Active Template Library obejmuje następujące definicje typów.

|||
|-|-|
|[_ATL_BASE_MODULE](#_atl_base_module)|Zdefiniowane jako element typedef na podstawie [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).|
|[_ATL_COM_MODULE](#_atl_com_module)|Zdefiniowane jako element typedef na podstawie [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).|
|[_ATL_MODULE](#_atl_module)|Zdefiniowane jako element typedef na podstawie [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).|
|[_ATL_WIN_MODULE](#_atl_win_module)|Zdefiniowane jako element typedef na podstawie [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|
|[ATL_URL_PORT](#atl_url_port)|Typ używany przez [zwinięcie](../../atl/reference/curl-class.md) do określenia numeru portu.|
|[CComDispatchDriver](#ccomdispatchdriver)|Ta klasa zarządza wskaźnikami interfejsu COM.|
|[CComGlobalsThreadModel](#ccomglobalsthreadmodel)|Wywołuje odpowiednie metody modelu wątku, niezależnie od używanego modelu wątkowego.|
|[CComObjectThreadModel](#ccomobjectthreadmodel)|Wywołuje odpowiednie metody modelu wątku, niezależnie od używanego modelu wątkowego.|
|[CContainedWindow](#ccontainedwindow)|Ta klasa jest specjalizacją `CContainedWindowT`.|
|[CPath](#cpath)|Specjalizacja [CPathT](../../atl/reference/cpatht-class.md) przy użyciu `CString`.|
|[CPathA](#cpatha)|Specjalizacja [CPathT](../../atl/reference/cpatht-class.md) przy użyciu `CStringA`.|
|[CPathW](#cpathw)|Specjalizacja [CPathT](../../atl/reference/cpatht-class.md) przy użyciu `CStringW`.|
|[CSimpleValArray](#csimplevalarray)|Reprezentuje tablicę do przechowywania typów prostych.|
|[DefaultThreadTraits](#defaultthreadtraits)|Domyślna klasa cech wątku.|
|[LPCURL](#lpcurl)|Wskaźnik do obiektu z stałym [zwinięciem](../../atl/reference/curl-class.md) .|
|[LPURL](#lpurl)|Wskaźnik do obiektu [zwinięcie](../../atl/reference/curl-class.md) .|

## <a name="_atl_base_module"></a><a name="_atl_base_module"></a>_ATL_BASE_MODULE

Zdefiniowane jako element typedef na podstawie _ATL_BASE_MODULE70.

```cpp
typedef ATL::_ATL_BASE_MODULE70 _ATL_BASE_MODULE;
```

### <a name="remarks"></a>Uwagi

Używany w każdym projekcie ATL. Na podstawie [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).

Klasy, które są częścią klas modułów ATL 7,0, pochodzą od struktury _ATL_BASE_MODULE.  Aby uzyskać więcej informacji o klasach modułów ATL, zobacz [klasy modułów com](../../atl/com-modules-classes.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlcore. h

## <a name="_atl_com_module"></a><a name="_atl_com_module"></a>_ATL_COM_MODULE

Zdefiniowane jako element typedef na podstawie _ATL_COM_MODULE70.

```cpp
typedef ATL::_ATL_COM_MODULE70 _ATL_COM_MODULE;
```

### <a name="remarks"></a>Uwagi

Używany przez projekty ATL korzystające z funkcji COM. Na podstawie [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

## <a name="_atl_module"></a><a name="_atl_module"></a>_ATL_MODULE

Zdefiniowane jako element typedef na podstawie _ATL_MODULE70.

```cpp
typedef ATL::_ATL_MODULE70 _ATL_MODULE;
```

### <a name="requirements"></a>Wymagania

**Nagłówki**

### <a name="remarks"></a>Uwagi

Na podstawie [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).

## <a name="_atl_win_module"></a><a name="_atl_win_module"></a>_ATL_WIN_MODULE

Zdefiniowane jako element typedef na podstawie _ATL_WIN_MODULE70.

```cpp
typedef ATL::_ATL_WIN_MODULE70 _ATL_WIN_MODULE;
```

### <a name="remarks"></a>Uwagi

Używane przez dowolne projekty ATL korzystające z funkcji okna. Na podstawie [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

## <a name="atl_url_port"></a><a name="atl_url_port"></a>ATL_URL_PORT

Typ używany przez [zwinięcie](curl-class.md) do określenia numeru portu.

```cpp
typedef WORD ATL_URL_PORT;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlutil. h

## <a name="ccomdispatchdriver"></a><a name="ccomdispatchdriver"></a>CComDispatchDriver

Ta klasa zarządza wskaźnikami interfejsu COM.

```cpp
typedef CComQIPtr<IDispatch, &__uuidof(IDispatch)> CComDispatchDriver;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

## <a name="ccomglobalsthreadmodel"></a><a name="ccomglobalsthreadmodel"></a>CComGlobalsThreadModel

Wywołuje odpowiednie metody modelu wątku, niezależnie od używanego modelu wątkowego.

```cpp
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

W zależności od modelu wątkowości używanego przez `CComGlobalsThreadModel` aplikację nazwa **typedef** odwołuje się do [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) lub [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Klasy te zawierają dodatkowe `typedef` nazwy do odwoływania się do klasy sekcji krytycznej.

> [!NOTE]
> `CComGlobalsThreadModel`nie odwołuje się do klasy [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).

Użycie `CComGlobalsThreadModel` zwalnia użytkownika od określenia określonej klasy modelu wątkowego. Bez względu na używany model wątkowości odpowiednie metody będą wywoływane.

Oprócz `CComGlobalsThreadModel`, ATL zawiera nazwę **typedef** [CComObjectThreadModel](#ccomobjectthreadmodel). Klasa, do której odwołuje się każdy `typedef` , zależy od używanego modelu wątkowości, jak pokazano w poniższej tabeli:

| — klasa typedef|Pojedyncze wątki|Wątkowość apartamentu|Bezpłatna wątkowość|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`; M =`CComMultiThreadModel`

Użyj `CComObjectThreadModel` wewnątrz klasy jednego obiektu. Użyj `CComGlobalsThreadModel` w obiekcie, który jest globalnie dostępny dla programu, lub jeśli chcesz chronić zasoby modułu w wielu wątkach.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

## <a name="ccomobjectthreadmodel"></a><a name="ccomobjectthreadmodel"></a>CComObjectThreadModel

Wywołuje odpowiednie metody modelu wątku, niezależnie od używanego modelu wątkowego.

```cpp
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

W zależności od modelu wątkowości używanego `typedef` przez aplikację nazwa `CComObjectThreadModel` odwołuje się do [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) lub [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Klasy te zawierają dodatkowe `typedef` nazwy do odwoływania się do klasy sekcji krytycznej.

> [!NOTE]
> `CComObjectThreadModel`nie odwołuje się do klasy [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).

Użycie `CComObjectThreadModel` zwalnia użytkownika od określenia określonej klasy modelu wątkowego. Bez względu na używany model wątkowości odpowiednie metody będą wywoływane.

Oprócz `CComObjectThreadModel`, ATL zawiera nazwę **typedef** [CComGlobalsThreadModel](#ccomglobalsthreadmodel). Klasa, do której odwołuje się każdy **element typedef** , zależy od używanego modelu wątkowości, jak pokazano w poniższej tabeli:

| — klasa typedef|Pojedyncze wątki|Wątkowość apartamentu|Bezpłatna wątkowość|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`; M =`CComMultiThreadModel`

Użyj `CComObjectThreadModel` wewnątrz klasy jednego obiektu. Użyj `CComGlobalsThreadModel` w obiekcie, który jest globalnie dostępny dla programu, lub jeśli chcesz chronić zasoby modułu w wielu wątkach.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

## <a name="ccontainedwindow"></a><a name="ccontainedwindow"></a>CContainedWindow

Ta klasa jest specjalizacją `CContainedWindowT`.

```cpp
typedef CContainedWindowT<CWindow> CContainedWindow;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

### <a name="remarks"></a>Uwagi

`CContainedWindow`jest specjalizacją [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md). Jeśli chcesz zmienić klasę bazową lub cechy, użyj `CContainedWindowT` bezpośrednio.

## <a name="cpath"></a><a name="cpath"></a>CPath

Specjalizacja [CPathT](../../atl/reference/cpatht-class.md) przy użyciu `CString`.

```cpp
typedef CPathT<CString> CPath;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlpath. h

## <a name="cpatha"></a><a name="cpatha"></a>CPathA

Specjalizacja [CPathT](../../atl/reference/cpatht-class.md) przy użyciu `CStringA`.

```cpp
typedef CPathT<CStringA> CPathA;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlpath. h

## <a name="cpathw"></a><a name="cpathw"></a>CPathW

Specjalizacja [CPathT](../../atl/reference/cpatht-class.md) przy użyciu `CStringW`.

```cpp
typedef ATL::CPathT<CStringW> CPathW;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlpath. h

## <a name="csimplevalarray"></a><a name="csimplevalarray"></a>CSimpleValArray

Reprezentuje tablicę do przechowywania typów prostych.

```cpp
#define CSimpleValArray CSimpleArray
```

### <a name="remarks"></a>Uwagi

`CSimpleValArray`jest dostarczany do tworzenia tablic zawierających proste typy danych i zarządzania nimi. Jest to prosta #define [CSimpleArray](../../atl/reference/csimplearray-class.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlsimpcoll. h

## <a name="lpcurl"></a><a name="lpcurl"></a>LPCURL

Wskaźnik do obiektu z stałym [zwinięciem](../../atl/reference/curl-class.md) .

```cpp
typedef const CUrl* LPCURL;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlutil. h

## <a name="defaultthreadtraits"></a><a name="defaultthreadtraits"></a>DefaultThreadTraits

Domyślna klasa cech wątku.

### <a name="syntax"></a>Składnia

```cpp
#if defined(_MT)
   typedef CRTThreadTraits DefaultThreadTraits;
#else
   typedef Win32ThreadTraits DefaultThreadTraits;
#endif
```

## <a name="remarks"></a>Uwagi

Jeśli bieżący projekt używa wielowątkowej CRT, DefaultThreadTraits jest zdefiniowany jako CRTThreadTraits. W przeciwnym razie jest używany Win32ThreadTraits.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

## <a name="lpurl"></a><a name="lpurl"></a>LPURL

Wskaźnik do obiektu [zwinięcie](../../atl/reference/curl-class.md) .

```cpp
typedef CUrl* LPURL;
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlutil. h

## <a name="see-also"></a>Zobacz także

[Składniki ATL COM pulpitu](../../atl/atl-com-desktop-components.md)<br/>
[Funkcje](../../atl/reference/atl-functions.md)<br/>
[Zmienne globalne](../../atl/reference/atl-global-variables.md)<br/>
[Klasy i struktury](../../atl/reference/atl-classes.md)<br/>
[Makra](../../atl/reference/atl-macros.md)
