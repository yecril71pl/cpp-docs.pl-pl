---
title: Definicje typów ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
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
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9d721cefd20ae5eb208c74d973069fb9365273d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="atl-typedefs"></a>Definicje typów ATL
Biblioteki Active Template Library obejmuje następujące elementy TypeDef.  
  
|||  
|-|-|  
|[_ATL_BASE_MODULE](#_atl_base_module)|Zdefiniowany jako element typedef, na podstawie [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).|  
|[_ATL_COM_MODULE](#_atl_com_module)|Zdefiniowany jako element typedef, na podstawie [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).|  
|[_ATL_MODULE](#_atl_module)|Zdefiniowany jako element typedef, na podstawie [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).|  
|[_ATL_WIN_MODULE](#_atl_win_module)|Zdefiniowany jako element typedef, na podstawie [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|  
|[ATL_URL_PORT](#atl_url_port)|Typ użyty przez [CUrl](../../atl/reference/curl-class.md) służący do określania numeru portu.|  
|[CComDispatchDriver](#ccomdispatchdriver)|Ta klasa zarządza wskaźników interfejsów COM.|  
|[CComGlobalsThreadModel](#ccomglobalsthreadmodel)|Wywołuje metody modelu, niezależnie od używanego modelu wątkowości odpowiedniego wątku.|  
|[CComObjectThreadModel](#ccomobjectthreadmodel)|Wywołuje metody modelu, niezależnie od używanego modelu wątkowości odpowiedniego wątku.|  
|[CContainedWindow](#ccontainedwindow)|Ta klasa jest specjalizacją **CContainedWindowT.**|  
|[CPath](#cpath)|Specjalizacji [CPathT](../../atl/reference/cpatht-class.md) przy użyciu `CString`.|  
|[CPathA](#cpatha)|Specjalizacji [CPathT](../../atl/reference/cpatht-class.md) przy użyciu `CStringA`.|  
|[CPathW](#cpathw)|Specjalizacji [CPathT](../../atl/reference/cpatht-class.md) przy użyciu `CStringW`.|  
|[CSimpleValArray](#csimplevalarray)|Reprezentuje tablicę do przechowywania typów prostych.|  
|[DefaultThreadTraits](#defaultthreadtraits)|Domyślna klasa cech wątku.|  
|[LPCURL](#lpcurl)|Wskaźnik do wartości stałej [CUrl](../../atl/reference/curl-class.md) obiektu.|  
|[LPURL](#lpurl)|Wskaźnik do [CUrl](../../atl/reference/curl-class.md) obiektu.|  
  
##  <a name="_atl_base_module"></a>_ATL_BASE_MODULE  
 Zdefiniowane jako oparte na _ATL_BASE_MODULE70 typedef.  
  
```   
typedef ATL::_ATL_BASE_MODULE70 _ATL_BASE_MODULE;   
```  
  
### <a name="remarks"></a>Uwagi  
 Używane w każdym projekcie ATL. Na podstawie [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).  
  
 Klasy, które są częścią klasy modułów ALT 7.0 pochodzi ze struktury _ATL_BASE_MODULE.  Aby uzyskać więcej informacji na klasy modułów ALT dotyczą [klasy COM modułów](../../atl/com-modules-classes.md).  

## <a name="requirements"></a>Wymagania
**Nagłówek:** atlcore.h

##  <a name="_atl_com_module"></a>_ATL_COM_MODULE  
 Zdefiniowane jako oparte na _ATL_COM_MODULE70 typedef.  
  
```   
typedef ATL::_ATL_COM_MODULE70 _ATL_COM_MODULE;   
```  
  
### <a name="remarks"></a>Uwagi  
 Używany przez projektów ATL, korzystające z funkcji COM. Na podstawie [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).  

## <a name="requirements"></a>Wymagania
**Nagłówek:** atlbase.h
  
##  <a name="_atl_module"></a>_ATL_MODULE  
 Zdefiniowane jako oparte na _ATL_MODULE70 typedef.  
  
```   
typedef ATL::_ATL_MODULE70 _ATL_MODULE;   
```  
## <a name="requirements"></a>Wymagania
**Nagłówek:** 
  
### <a name="remarks"></a>Uwagi  
 Na podstawie [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).  
  
##  <a name="_atl_win_module"></a>_ATL_WIN_MODULE  
 Zdefiniowane jako oparte na _ATL_WIN_MODULE70 typedef.  
  
```   
typedef ATL::_ATL_WIN_MODULE70 _ATL_WIN_MODULE; 
 
```  
  
### <a name="remarks"></a>Uwagi  
 Używany przez wszystkie projekty ATL korzystające z funkcji obsługi okien. Na podstawie [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md).  

## <a name="requirements"></a>Wymagania
**Nagłówek:** atlbase.h 
  
##  <a name="atl_url_port"></a>ATL_URL_PORT 
  Typ użyty przez [CUrl](curl-class.md) służący do określania numeru portu.
```  
typedef WORD ATL_URL_PORT;
```  

## <a name="requirements"></a>Wymagania
**Nagłówek:** atlutil.h

##  <a name="ccomdispatchdriver"></a>CComDispatchDriver  
 Ta klasa zarządza wskaźników interfejsów COM.  
  
```   
typedef CComQIPtr<IDispatch, &__uuidof(IDispatch)> CComDispatchDriver;   
```  
## <a name="requirements"></a>Wymagania
**Nagłówek:** atlbase.h
  
##  <a name="ccomglobalsthreadmodel"></a>CComGlobalsThreadModel  
 Wywołuje metody modelu, niezależnie od używanego modelu wątkowości odpowiedniego wątku.  
  
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
 W zależności od modelu wątkowości używanych przez aplikację `typedef` nazwa `CComGlobalsThreadModel` albo odwołuje się do [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) lub [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Te klasy zapewnić dodatkowe `typedef` nazwy do odwołuje się do klasy sekcja krytyczna.  
  
> [!NOTE]
> `CComGlobalsThreadModel`nie odwołuje się do klasy [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).  
  
 Przy użyciu `CComGlobalsThreadModel` zwalnia z określania określonej klasy modelu wątkowości. Niezależnie od używanego modelu wątkowości zostanie wywołana odpowiednie metody.  
  
 Oprócz `CComGlobalsThreadModel`, zapewnia ATL `typedef` nazwa [CComObjectThreadModel](#ccomobjectthreadmodel). Klasa odwołuje się każdego `typedef` zależy model wątkowy używany, jak pokazano w poniższej tabeli:  
  
|— klasa typedef|Pojedynczy wątkowość|Wątkowości typu apartment|Wolnych wątków|  
|-------------|----------------------|-------------------------|--------------------|  
|`CComObjectThreadModel`|S|S|M|  
|`CComGlobalsThreadModel`|S|M|M|  
  
 S = `CComSingleThreadModel`; M =`CComMultiThreadModel`  
  
 Użyj `CComObjectThreadModel` w obrębie klasy pojedynczego obiektu. Użyj `CComGlobalsThreadModel` w obiekcie, który jest ogólnie dostępna dla programu, lub jeśli chcesz chronić modułu zasobów przez wiele wątków.  

## <a name="requirements"></a>Wymagania
**Nagłówek:** atlbase.h
  
##  <a name="ccomobjectthreadmodel"></a>CComObjectThreadModel  
 Wywołuje metody modelu, niezależnie od używanego modelu wątkowości odpowiedniego wątku.  
  
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
 W zależności od modelu wątkowości używanych przez aplikację `typedef` nazwa `CComObjectThreadModel` albo odwołuje się do [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) lub [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Te klasy zapewnić dodatkowe `typedef` nazwy do odwołuje się do klasy sekcja krytyczna.  
  
> [!NOTE]
> `CComObjectThreadModel`nie odwołuje się do klasy [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).  
  
 Przy użyciu `CComObjectThreadModel` zwalnia z określania określonej klasy modelu wątkowości. Niezależnie od używanego modelu wątkowości zostanie wywołana odpowiednie metody.  
  
 Oprócz `CComObjectThreadModel`, zapewnia ATL `typedef` nazwa [CComGlobalsThreadModel](#ccomglobalsthreadmodel). Klasa odwołuje się każdego `typedef` zależy model wątkowy używany, jak pokazano w poniższej tabeli:  
  
|— klasa typedef|Pojedynczy wątkowość|Wątkowości typu apartment|Wolnych wątków|  
|-------------|----------------------|-------------------------|--------------------|  
|`CComObjectThreadModel`|S|S|M|  
|`CComGlobalsThreadModel`|S|M|M|  
  
 S = `CComSingleThreadModel`; M =`CComMultiThreadModel`  
  
 Użyj `CComObjectThreadModel` w obrębie klasy pojedynczego obiektu. Użyj `CComGlobalsThreadModel` w obiekt, który jest ogólnie dostępna do programu, lub jeśli chcesz chronić zasoby modułu przez wiele wątków.  

## <a name="requirements"></a>Wymagania
**Nagłówek:** atlbase.h
  
##  <a name="ccontainedwindow"></a>CContainedWindow  
 Ta klasa jest specjalizacją **CContainedWindowT.**  
  
```   
typedef CContainedWindowT<CWindow> CContainedWindow;   
```  

## <a name="requirements"></a>Wymagania
**Nagłówek:** atlwin.h
  
### <a name="remarks"></a>Uwagi  
 `CContainedWindow`jest [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md). Jeśli chcesz zmienić cechy lub klasy podstawowej, użyj `CContainedWindowT` bezpośrednio.  
  
##  <a name="cpath"></a>CPath  
 Specjalizacji [CPathT](../../atl/reference/cpatht-class.md) przy użyciu `CString`.  
  
```   
typedef CPathT<CString> CPath;   
```  

## <a name="requirements"></a>Wymagania
**Nagłówek:** atlpath.h
  
##  <a name="cpatha"></a>CPathA  
 Specjalizacji [CPathT](../../atl/reference/cpatht-class.md) przy użyciu `CStringA`.  
  
```   
typedef CPathT<CStringA> CPathA;   
```

## <a name="requirements"></a>Wymagania
**Nagłówek:** atlpath.h  
  
##  <a name="cpathw"></a>CPathW  
 Specjalizacji [CPathT](../../atl/reference/cpatht-class.md) przy użyciu `CStringW`.  
  
```   
typedef ATL::CPathT<CStringW> CPathW;   
```  
## <a name="requirements"></a>Wymagania
**Nagłówek:** atlpath.h
  
##  <a name="csimplevalarray"></a>CSimpleValArray  
 Reprezentuje tablicę do przechowywania typów prostych.  
  
```   
#define CSimpleValArray CSimpleArray   
```  

  
### <a name="remarks"></a>Uwagi  
 `CSimpleValArray`jest dostępne w celu tworzenia i zarządzania tablicami zawierający proste typy danych. Jest prostą #define z [CSimpleArray](../../atl/reference/csimplearray-class.md).  


## <a name="requirements"></a>Wymagania
**Nagłówek:** atlsimpcoll.h
  
##  <a name="lpcurl"></a>LPCURL  
 Wskaźnik do wartości stałej [CUrl](../../atl/reference/curl-class.md) obiektu.  
  
```   
typedef const CUrl* LPCURL;   
```  

## <a name="requirements"></a>Wymagania
**Nagłówek:** atlutil.h

##  <a name="defaultthreadtraits"></a>DefaultThreadTraits
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
  
##  <a name="lpurl"></a>LPURL  
 Wskaźnik do [CUrl](../../atl/reference/curl-class.md) obiektu.  
  
```   
typedef CUrl* LPURL;   
```  

## <a name="requirements"></a>Wymagania
**Nagłówek:** atlutil.h


## <a name="see-also"></a>Zobacz też  
 [Składniki COM pulpitu ATL](../../atl/atl-com-desktop-components.md)   
 [Funkcje](../../atl/reference/atl-functions.md)   
 [Zmienne globalne](../../atl/reference/atl-global-variables.md)   
 [Struktury](../../atl/reference/atl-structures.md)   
 [Makra](../../atl/reference/atl-macros.md)   
 [Klasy](../../atl/reference/atl-classes.md)