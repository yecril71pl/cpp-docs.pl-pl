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
ms.openlocfilehash: 8492127af8a1267da3beed678f8a66424ba26442
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483401"
---
# <a name="catlautothreadmodulet-class"></a>Klasa CAtlAutoThreadModuleT

Ta klasa dostarcza metody do implementowania serwera wątków w puli, model przedziału COM.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template <class T,
         class ThreadAllocator = CComSimpleThreadAllocator,
         DWORD dwWait = INFINITE>
class ATL_NO_VTABLE CAtlAutoThreadModuleT : public IAtlAutoThreadModule
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasa, który będzie implementowany serwer COM.

*ThreadAllocator*<br/>
Klasa zarządzania wybór wątku. Wartość domyślna to [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

*dwWait*<br/>
Określa interwał limitu czasu w milisekundach. Wartość domyślna to NIESKOŃCZONE, co oznacza interwał limitu czasu metody nigdy nie upłynie.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlAutoThreadModuleT::GetDefaultThreads](#getdefaultthreads)|Ta funkcja statyczna dynamicznie oblicza i zwraca maksymalną liczbę wątków dla modułu "EXE", na podstawie liczby procesorów.|

## <a name="remarks"></a>Uwagi

Klasa [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) pochodzi od klasy `CAtlAutoThreadModuleT` w celu wdrożenia serwera wątków w puli, model przedziału COM. Zastępuje on programy przestarzałe klasy [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

> [!NOTE]
>  Ta klasa nie można używać w bibliotece DLL, jako domyślny *dwWait* wartości NIESKOŃCZONE spowoduje zakleszczenia, gdy biblioteka DLL jest zwalniana.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IAtlAutoThreadModule`

`CAtlAutoThreadModuleT`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="getdefaultthreads"></a>  CAtlAutoThreadModuleT::GetDefaultThreads

Ta funkcja statyczna dynamicznie oblicza i zwraca maksymalną liczbę wątków dla modułu "EXE", na podstawie liczby procesorów.

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>Wartość zwracana

Liczba wątków, które zostały utworzone w EXE module.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę metodę, jeśli chcesz użyć innej metody do obliczania liczby wątków. Domyślnie liczba wątków zależy od liczby procesorów.

## <a name="see-also"></a>Zobacz też

[Klasa IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)<br/>
[Klasa IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Klasy modułów](../../atl/atl-module-classes.md)
