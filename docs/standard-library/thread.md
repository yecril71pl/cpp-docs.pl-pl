---
title: "&lt;Wątek&gt; | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- <thread>
dev_langs:
- C++
ms.assetid: 0c858405-4efb-449d-bf76-70d3693c9234
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fa16f2f06a55122619741c5889f41ce3d6b53c1e
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ltthreadgt"></a>&lt;wątek&gt;
Dołącz nagłówek standardowy \<wątku > w celu zdefiniowania klasy `thread` i różne funkcje pomocnicze.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
#include <thread>  
```  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  W kodzie, który ma być kompilowana przy użyciu **/CLR**, ten nagłówek jest zablokowany.  
  
 `__STDCPP_THREADS__` Makro jest zdefiniowany jako wartość niezerową, aby wskazać, że wątki są obsługiwane przez ten nagłówek.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-classes"></a>Klas publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[thread, klasa](../standard-library/thread-class.md)|Definiuje obiekt, który służy do obserwować i zarządzanie nimi wątku do wykonania w aplikacji.|  
  
### <a name="public-structures"></a>Publiczny struktury  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[hash, struktura (Standardowa biblioteka C++)](../standard-library/hash-structure-stl.md)|Definiuje funkcję elementu członkowskiego, która zwraca wartość, która unikatowo jest określany przez `thread::id`. Definiuje funkcję elementu członkowskiego [skrótu](../standard-library/hash-class.md) funkcji, które jest odpowiednie dla wartości mapowanie typu `thread::id` dystrybucji wartości indeksu.|  
  
### <a name="public-functions"></a>Funkcje publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[get_id](../standard-library/thread-functions.md#get_id)|Unikatowy identyfikator bieżącego wątku do wykonania.|  
|[sleep_for](../standard-library/thread-functions.md#sleep_for)|Blokuje wątek wywołujący.|  
|[sleep_until](../standard-library/thread-functions.md#sleep_until)|Blokuje wątek wywołujący co najmniej do określonego czasu.|  
|[swap](../standard-library/thread-functions.md#swap)|Zamienia stanów dwóch `thread` obiektów.|  
|[yield](../standard-library/thread-functions.md#yield)|Sygnały do innych wątków systemu operacyjnego, nawet wtedy, gdy bieżący wątek zazwyczaj będzie nadal działał.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[operator > = — Operator](../standard-library/thread-operators.md#op_gt_eq)|Określa, czy co najmniej `thread::id` obiektu jest większa lub równa innej.|  
|[operator > — Operator](../standard-library/thread-operators.md#op_gt)|Określa, czy co najmniej `thread::id` obiekt jest większy niż innym.|  
|[Operator < = — Operator](../standard-library/thread-operators.md#op_lt_eq)|Określa, czy co najmniej `thread::id` obiekt jest mniejszy niż lub równy do innego.|  
|[Operator < — Operator](../standard-library/thread-operators.md#op_lt)|Określa, czy co najmniej `thread::id` obiekt jest mniejszy niż innym.|  
|[operator! = — Operator](../standard-library/thread-operators.md#op_neq)|Porównuje dwa `thread::id` obiekty pod kątem nierówności.|  
|[operator== Operator](../standard-library/thread-operators.md#op_eq_eq)|Porównuje dwa `thread::id` obiekty pod kątem równości.|  
|[Operator << — Operator](../standard-library/thread-operators.md#op_lt_lt)|Wstawia tekst reprezentację `thread::id` obiektu do strumienia.|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

