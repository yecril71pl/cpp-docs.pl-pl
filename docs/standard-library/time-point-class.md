---
title: "time_point — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- chrono/std::chrono::time_point
- chrono/std::chrono::time_point::time_point
- chrono/std::chrono::time_point::max
- chrono/std::chrono::time_point::min
- chrono/std::chrono::time_point::time_since_epoch
dev_langs:
- C++
ms.assetid: 18be1e52-57b9-489a-8a9b-f58894f0aaad
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::chrono [C++], time_point
ms.workload:
- cplusplus
ms.openlocfilehash: 4d81f49fd94dcedacfe33de75e307a441f74a94e
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="timepoint-class"></a>time_point — Klasa
A `time_point` opisuje typ, który reprezentuje punkt w czasie. Przechowuje obiekt typu [czas trwania](../standard-library/duration-class.md) który przechowuje czas, który upłynął od epoka reprezentowanego przez argument szablonu `Clock`.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class Clock,  
    class Duration = typename Clock::duration>  
class time_point;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`time_point::clock`|Synonim parametru szablonu `Clock`.|  
|`time_point::duration`|Synonim parametru szablonu `Duration`.|  
|`time_point::period`|Synonim dla nazwy typu zagnieżdżonego `duration::period`.|  
|`time_point::rep`|Synonim dla nazwy typu zagnieżdżonego `duration::rep`.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[time_point](#time_point)|Konstruuje `time_point` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[max](#max)|Określa górne ograniczenie dla `time_point::ref`.|  
|[min](#min)|Określa dolną granicę dla `time_point::ref`.|  
|[time_since_epoch](#time_since_epoch)|Zwraca zapisana `duration` wartość.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[time_point::operator+=](#op_add_eq)|Dodaje określoną wartość do składowanej czasu trwania.|  
|[time_point::operator-=](#operator-_eq)|Odejmuje określoną wartość z przechowywanych czasu trwania.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<chrono >  
  
 **Namespace:** std::chrono  
  
##  <a name="max"></a>  time_point::Max
 Metoda statyczna, która zwraca górną granicę dla wartości typu `time_point::ref`.  
  
```  
static constexpr time_point max();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 W efekcie zwraca `time_point(duration::max())`.  
  
##  <a name="min"></a>  time_point::min
 Statyczną metodę, która zwraca ograniczeniem dla wartości typu `time_point::ref`.  
  
```  
static constexpr time_point min();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 W efekcie zwraca `time_point(duration::min())`.  
  
##  <a name="op_add_eq"></a>  time_point::operator +=  
 Dodaje określoną wartość do składowanej [czas trwania](../standard-library/duration-class.md) wartość.  
  
```  
time_point& operator+=(const duration& Dur);
```  
  
### <a name="parameters"></a>Parametry  
 `Dur`  
 A `duration` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `time_point` Obiektu po wykonaniu operacji dodawania.  
  
##  <a name="time_point__operator-_eq"></a>  time_point::operator-=  
 Odejmuje określoną wartość z przechowywanych [czas trwania](../standard-library/duration-class.md) wartość.  
  
```  
time_point& operator-=(const duration& Dur);
```  
  
### <a name="parameters"></a>Parametry  
 `Dur`  
 A `duration` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `time_point` Obiektu po wykonaniu odejmowania.  
  
##  <a name="time_point"></a>  time_point::time_point — Konstruktor  
 Konstruuje `time_point` obiektu.  
  
```  
constexpr time_point();

constexpr explicit time_point(const duration& Dur);

template <class Duration2>  
constexpr time_point(const time_point<clock, Duration2>& Tp);
```  
  
### <a name="parameters"></a>Parametry  
 `Dur`  
 A [czas trwania](../standard-library/duration-class.md) obiektu.  
  
 `Tp`  
 A `time_point` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy Konstruktor konstrukcji obiektu których przechowywane `duration` wartość jest równa [duration::zero](../standard-library/duration-class.md#zero).  
  
 Drugi Konstruktor tworzy obiekt jest taki sam, którego wartość czasu trwania przechowywanych `Dur`. O ile `is_convertible<Duration2, duration>` *jest spełniony*, drugi Konstruktor nie uczestniczy w Rozpoznanie przeciążenia. Aby uzyskać więcej informacji, zobacz [< type_traits >](../standard-library/type-traits.md).  
  
 Trzeci Konstruktor inicjuje jego `duration` wartość przy użyciu `Tp.time_since_epoch()`.  
  
##  <a name="time_since_epoch"></a>  time_point::time_since_epoch
 Pobiera zapisana [czas trwania](../standard-library/duration-class.md) wartość.  
  
```  
constexpr duration time_since_epoch() const;
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono>](../standard-library/chrono.md)

