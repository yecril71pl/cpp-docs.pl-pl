---
title: Klasa CAtlAutoThreadModuleT | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT::GetDefaultThreads
dev_langs: C++
helpviewer_keywords: CAtlAutoThreadModuleT class
ms.assetid: ae1667c6-3fb8-47bc-b35d-9ea5e9896d7f
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 594e6bd026d214e2dd5d12e702d26a5942cfc872
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="catlautothreadmodulet-class"></a>Klasa CAtlAutoThreadModuleT
Ta klasa dostarcza metody wykonywania wątków w puli, modelu typu apartment serwer COM.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T, 
         class ThreadAllocator = CComSimpleThreadAllocator,
         DWORD dwWait = INFINITE>  
class ATL_NO_VTABLE CAtlAutoThreadModuleT : public IAtlAutoThreadModule
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Klasy, która będzie implementowany serwer COM.  
  
 `ThreadAllocator`  
 Klasa zarządzania wyboru wątku. Wartość domyślna to [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).  
  
 `dwWait`  
 Określa interwał limitu czasu w milisekundach. Wartość domyślna to bez ograniczeń czasowych, co oznacza metodę limitu czasu nigdy nie upłynie.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlAutoThreadModuleT::GetDefaultThreads](#getdefaultthreads)|Ta funkcja statyczna dynamicznie oblicza i zwraca maksymalną liczbę wątków dla modułu EXE, na podstawie liczby procesorów.|  
  
## <a name="remarks"></a>Uwagi  
 Klasa [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) pochodną `CAtlAutoThreadModuleT` w celu wdrożenia serwera COM wątków w puli, modelu typu apartment. Zastępuje przestarzałej klasy [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).  
  
> [!NOTE]
>  Ta klasa nie stosuje się w biblioteki DLL, domyślnie `dwWait` wartość INFINITE spowoduje zakleszczenie, gdy biblioteka DLL jest zwolniony.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IAtlAutoThreadModule`  
  
 `CAtlAutoThreadModuleT`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
##  <a name="getdefaultthreads"></a>CAtlAutoThreadModuleT::GetDefaultThreads  
 Ta funkcja statyczna dynamicznie oblicza i zwraca maksymalną liczbę wątków dla modułu EXE, na podstawie liczby procesorów.  
  
```
static int GetDefaultThreads();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba wątków, które mogą być tworzone w EXE module.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę metodę, jeśli chcesz użyć innej metody do obliczania liczby wątków. Domyślnie to liczba wątków opiera się na liczbę procesorów.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Klasa IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)   
 [Klasy modułów](../../atl/atl-module-classes.md)
