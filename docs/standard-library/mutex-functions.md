---
title: '&lt;mutex&gt; funkcje i zmienne | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- mutex/std::adopt_lock
- mutex/std::call_once
- mutex/std::defer_lock
- mutex/std::lock
- mutex/std::try_to_lock
ms.assetid: 78ab3c8b-c7db-4226-ac93-e2e78ff8b964
caps.latest.revision: 
manager: ghogen
helpviewer_keywords:
- std::adopt_lock [C++]
- std::call_once [C++]
- std::defer_lock [C++]
- std::lock [C++]
- std::try_to_lock [C++]
ms.openlocfilehash: 8fcee8ec1313a153764c94a709e32b3a6109b576
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ltmutexgt-functions-and-variables"></a>&lt;mutex&gt; funkcje i zmienne
||||  
|-|-|-|  
|[adopt_lock](#adopt_lock)|[call_once](#call_once)|[defer_lock](#defer_lock)|  
|[lock](#lock)|[try_to_lock](#try_to_lock)|  
  
##  <a name="adopt_lock"></a>  adopt_lock — zmienna  
 Reprezentuje obiekt, który może być przekazane do konstruktorów dla [lock_guard](../standard-library/lock-guard-class.md) i [unique_lock](../standard-library/unique-lock-class.md) aby wskazać, że obiektu mutex, który również jest przekazywany do konstruktora jest zablokowany.  
  
```cpp  
const adopt_lock_t adopt_lock;
```  
  
##  <a name="call_once"></a>  call_once —  
 Udostępnia mechanizm wywoływania dokładnie raz określony obiekt można wywołać podczas wykonywania.  
  
```
template <class Callable, class... Args>
void call_once(once_flag& Flag,
    Callable F&&, Args&&... A);
```  
  
### <a name="parameters"></a>Parametry  
 `Flag`  
 A [once_flag —](../standard-library/once-flag-structure.md) obiekt, który zapewnia, że można wywołać obiektu jest wywołana tylko raz.  
  
 `F`  
 Można wywołać obiektu.  
  
 `A`  
 Lista argumentów.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `Flag` jest nieprawidłowa, funkcja zwraca [system_error —](../standard-library/system-error-class.md) mający z kodem błędu `invalid_argument`. W przeciwnym razie używa funkcji szablonu jego `Flag` argumentu, aby upewnić się, że wymaga `F(A...)` pomyślnie tylko raz, niezależnie od tego, ile razy szablonu wywołania funkcji. Jeśli `F(A...)` wyjścia przez Zgłaszanie wyjątku, wywołanie zakończyła się niepowodzeniem.  
  
##  <a name="defer_lock"></a>  defer_lock — zmienna  
 Reprezentuje obiekt, który może zostać przekazany do konstruktora dla [unique_lock](../standard-library/unique-lock-class.md). Oznacza to, że konstruktora nie powinna zablokować obiektu mutex, który również jest przekazywany do niego.  
  
```cpp  
const defer_lock_t defer_lock;
```  
  
##  <a name="lock"></a>  blokady  
 Próbuje zablokować wszystkie argumenty bez zakleszczenia.  
  
```cpp  
template <class L1, class L2, class... L3>
void lock(L1&, L2&, L3&...);
```  
  
### <a name="remarks"></a>Uwagi  
 Argumenty funkcji szablonu musi być *typów obiektu mutex*, z wyjątkiem tego, który odwołuje się do `try_lock` może zgłaszać wyjątków.  
  
 Funkcja blokuje wszystkie argumenty bez zakleszczenie wywołań `lock`, `try_lock`, i `unlock`. Jeśli wywołanie `lock` lub `try_lock` zgłasza wyjątek, wywołania funkcji `unlock` na dowolny obiekt mutex, które pomyślnie zostały zablokowane przed ponowne generowanie wyjątek.  
  
##  <a name="try_to_lock"></a>  try_to_lock — zmienna  
 Reprezentuje obiekt, który może zostać przekazany do konstruktora dla [unique_lock](../standard-library/unique-lock-class.md) wskazująca, czy konstruktora należy dążyć do odblokowania `mutex` który jest również przekazywany do niego bez blokowania.  
  
```cpp  
const try_to_lock_t try_to_lock;
```  
  
## <a name="see-also"></a>Zobacz też  
 [\<mutex>](../standard-library/mutex.md)



