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
ms.openlocfilehash: 7308e3a51c531fbe942e2df326c03273eeb326e2
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168726"
---
# <a name="catlautothreadmodulet-class"></a>Klasa CAtlAutoThreadModuleT

Ta klasa zawiera metody implementacji serwera COM w puli wątków, który jest modelem typu Apartment.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```cpp
template <class T,
         class ThreadAllocator = CComSimpleThreadAllocator,
         DWORD dwWait = INFINITE>
class ATL_NO_VTABLE CAtlAutoThreadModuleT : public IAtlAutoThreadModule
```

### <a name="parameters"></a>Parametry

*T*<br/>
Klasa, która będzie implementować serwer COM.

*ThreadAllocator*<br/>
Klasa, która zarządza wyborem wątku. Wartość domyślna to [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

*dwWait*<br/>
Określa interwał limitu czasu (w milisekundach). Wartość domyślna to NIESKOŃCZONość, co oznacza, że nigdy nie upłynął limit czasu metody.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlAutoThreadModuleT::GetDefaultThreads](#getdefaultthreads)|Ta funkcja statyczna dynamicznie oblicza i zwraca maksymalną liczbę wątków dla modułu EXE na podstawie liczby procesorów.|

## <a name="remarks"></a>Uwagi

Klasa [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) dziedziczy z `CAtlAutoThreadModuleT` , aby zaimplementować serwer com z pulą wątków, model typu Apartment. Zastępuje przestarzałą klasę [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

> [!NOTE]
> Tej klasy nie należy używać w bibliotece DLL, ponieważ domyślna wartość *DWWAIT* nieskończoność spowoduje zakleszczenie, gdy biblioteka DLL zostanie zwolniona.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IAtlAutoThreadModule`

`CAtlAutoThreadModuleT`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

## <a name="catlautothreadmoduletgetdefaultthreads"></a><a name="getdefaultthreads"></a>CAtlAutoThreadModuleT::GetDefaultThreads

Ta funkcja statyczna dynamicznie oblicza i zwraca maksymalną liczbę wątków dla modułu EXE na podstawie liczby procesorów.

```cpp
static int GetDefaultThreads();
```

### <a name="return-value"></a>Wartość zwracana

Liczba wątków, które mają zostać utworzone w module EXE.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, jeśli chcesz użyć innej metody do obliczania liczby wątków. Domyślnie liczba wątków jest oparta na liczbie procesorów.

## <a name="see-also"></a>Zobacz także

[Klasa IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasa IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Klasy modułów](../../atl/atl-module-classes.md)
