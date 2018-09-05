---
title: Klasa CAtlAutoThreadModuleT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT::GetDefaultThreads
dev_langs:
- C++
helpviewer_keywords:
- CAtlAutoThreadModuleT class
ms.assetid: ae1667c6-3fb8-47bc-b35d-9ea5e9896d7f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ebf3ba07ac5608a47f4e2bbbe853cb37c033e5f7
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43757618"
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

*T*  
Klasa, który będzie implementowany serwer COM.

*ThreadAllocator*  
Klasa zarządzania wybór wątku. Wartość domyślna to [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

*dwWait*  
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

[Klasa IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)   
[Klasa — Przegląd](../../atl/atl-class-overview.md)   
[Klasa IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)   
[Klasy modułów](../../atl/atl-module-classes.md)
