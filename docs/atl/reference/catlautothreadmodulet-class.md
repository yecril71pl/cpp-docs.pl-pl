---
title: Klasa CAtlAutoThreadModuleT
ms.date: 11/04/2016
f1_keywords:
- CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT::GetDefaultThreads
helpviewer_keywords:
- CAtlAutoThreadModuleT class
ms.assetid: ae1667c6-3fb8-47bc-b35d-9ea5e9896d7f
ms.openlocfilehash: e7b7a327d7c47c4472b43ed58fbe9ad0556a7620
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321542"
---
# <a name="catlautothreadmodulet-class"></a>Klasa CAtlAutoThreadModuleT

Ta klasa udostępnia metody implementacji serwera COM z puli wątków.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class T,
         class ThreadAllocator = CComSimpleThreadAllocator,
         DWORD dwWait = INFINITE>
class ATL_NO_VTABLE CAtlAutoThreadModuleT : public IAtlAutoThreadModule
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasa, która zaimplementuje serwer COM.

*Lokalizator gwintów*<br/>
Klasa zarządzająca wyborem wątku. Wartością domyślną jest [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

*dwWait (Niem.*<br/>
Określa interwał przesuwu w milisekundach. Wartość domyślna to INFINITE, co oznacza, że interwał przekroju czasu metody nigdy nie ulatnia się.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlAutoThreadModuleT::GetDefaultWreads](#getdefaultthreads)|Ta funkcja statyczna dynamicznie oblicza i zwraca maksymalną liczbę wątków dla modułu EXE na podstawie liczby procesorów.|

## <a name="remarks"></a>Uwagi

Klasa [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) pochodzi `CAtlAutoThreadModuleT` od w celu zaimplementowania wątku puli, model mieszkania serwera COM. Zastępuje przestarzałą klasę [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

> [!NOTE]
> Ta klasa nie powinna być używana w biblioteki DLL, ponieważ domyślna wartość *dwWait* INFINITE spowoduje zakleszczenie, gdy biblioteka DLL jest zwalniana.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IAtlAutoThreadModule`

`CAtlAutoThreadModuleT`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="catlautothreadmoduletgetdefaultthreads"></a><a name="getdefaultthreads"></a>CAtlAutoThreadModuleT::GetDefaultWreads

Ta funkcja statyczna dynamicznie oblicza i zwraca maksymalną liczbę wątków dla modułu EXE na podstawie liczby procesorów.

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>Wartość zwracana

Liczba wątków, które mają zostać utworzone w module EXE.

### <a name="remarks"></a>Uwagi

Zastąd w tej metodzie należy użyć innej metody obliczania liczby wątków. Domyślnie liczba wątków jest oparta na liczbie procesorów.

## <a name="see-also"></a>Zobacz też

[Klasa IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasa IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Klasy modułów](../../atl/atl-module-classes.md)
