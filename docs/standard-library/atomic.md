---
title: '&lt;Atomic&gt; | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- <atomic>
- atomic/std::atomic_int_least32_t
- atomic/std::atomic_ullong
- atomic/std::atomic_ptrdiff_t
- atomic/std::atomic_char16_t
- atomic/std::atomic_schar
- atomic/std::atomic_ulong
- atomic/std::atomic_uint_fast32_t
- atomic/std::atomic_uint8_t
- atomic/std::atomic_int32_t
- atomic/std::atomic_uint_fast64_t
- atomic/std::atomic_uint32_t
- atomic/std::atomic_int16_t
- atomic/std::atomic_uintmax_t
- atomic/std::atomic_intmax_t
- atomic/std::atomic_long
- atomic/std::atomic_int
- atomic/std::atomic_uint_least8_t
- atomic/std::atomic_size_t
- atomic/std::atomic_uint_fast16_t
- atomic/std::atomic_wchar_t
- atomic/std::atomic_int_fast64_t
- atomic/std::atomic_uint_fast8_t
- atomic/std::atomic_int_fast8_t
- atomic/std::atomic_intptr_t
- atomic/std::atomic_uint
- atomic/std::atomic_uint16_t
- atomic/std::atomic_char32_t
- atomic/std::atomic_uint64_t
- atomic/std::atomic_ushort
- atomic/std::atomic_int_least16_t
- atomic/std::atomic_char
- atomic/std::atomic_uint_least32_t
- atomic/std::atomic_uintptr_t
- atomic/std::atomic_short
- atomic/std::atomic_llong
- atomic/std::atomic_uint_least16_t
- atomic/std::atomic_int_fast16_t
- atomic/std::atomic_int_least8_t
- atomic/std::atomic_int_least64_t
- atomic/std::atomic_int_fast32_t
- atomic/std::atomic_uchar
- atomic/std::atomic_int8_t
- atomic/std::atomic_int64_t
- atomic/std::atomic_uint_least64_t
dev_langs:
- C++
ms.assetid: e79a6b9f-52ff-48da-9554-654c4e1999f6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dd543003e7edba4e1766efc11670fd6e505820bb
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ltatomicgt"></a>&lt;atomic&gt;
Definiuje klasy i klasy szablonu na potrzeby tworzenia typów, które obsługują operacjach niepodzielnych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
#include <atomic>  
```  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  W kodzie, który ma być kompilowana przy użyciu **/CLR**, ten nagłówek jest zablokowany.  
  
 Operacją niepodzielną ma dwie właściwości klucza, które ułatwiają poprawnie zaznaczać obiektu bez korzystania z blokady obiektu mutex za pomocą wielu wątków.  
  
-   Ponieważ operacją niepodzielną niepodzielnych, drugi niepodzielną operację na ten sam obiekt z innym wątku można uzyskać stanu obiektu tylko przed lub po pierwszym niepodzielną operację.  
  
-   Na podstawie jego [memory_order](../standard-library/atomic-enums.md#memory_order_enum) argumentu, operacją niepodzielną ustanawia porządkowanie wymagania w przypadku widoczności skutków innych operacji niepodzielnych w tym samym wątku. W rezultacie umożliwia zablokowanie optymalizacje kompilatora, które narusza wymagania porządkowania.  
  
 Na niektórych platformach może nie być możliwe wydajnie implementacji operacji niepodzielnych w przypadku niektórych typów bez użycia `mutex` blokad. Jest typem niepodzielnym *zwolnić blokady* blokad użycie żadne niepodzielne operacje tego typu.  
  
 **C ++ 11**: W obsłudze sygnału można wykonać operacji niepodzielnych w obiekcie `obj` Jeśli `obj.is_lock_free()` lub `atomic_is_lock_free(x)` mają wartość true.  
  
 Klasa [atomic_flag —](../standard-library/atomic-flag-structure.md) zawiera minimalne atomic typ, który przechowuje `bool` flagi. Jej operacje są zawsze zwolnić blokady.  
  
 Klasy szablonów `atomic<T>` przechowuje obiekt typu argumentu `T` i zapewnia atomic dostęp do tego przechowywana wartość. Można utworzyć przy użyciu dowolnego typu, który może zostać skopiowana przy użyciu [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) i sprawdzane pod kątem równości przy użyciu [funkcji memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md). W szczególności umożliwia z typami zdefiniowane przez użytkownika, które spełniają te wymagania i w wielu przypadkach z typów zmiennoprzecinkowych.  
  
 Szablon ma również zestaw specjalizacje dla typów całkowitych i częściowa specjalizacja dla wskaźników. Te specjalizacje zapewniają dodatkowe operacje, które nie są dostępne za pośrednictwem szablonu podstawowego.  
  
## <a name="pointer-specializations"></a>Wskaźnik specjalizacji  
 `atomic<T *>` Częściowe specjalizacje stosowana dla wszystkich typów wskaźnika. Udostępniają one metody arytmetyka wskaźnika.  
  
## <a name="integral-specializations"></a>Całkowite specjalizacji  
 `atomic<integral>` Specjalizacje dotyczą wszystkich typów całkowitych. Zapewniają one dodatkowe operacje, które nie są dostępne za pośrednictwem szablonu podstawowego.  
  
 Każdy `atomic<integral>` typ ma odpowiednie makra, które można używać w `if directive` do określenia w czasie kompilacji, czy operacje tego typu są bez blokady. Jeśli wartość tego makra wynosi zero, operacje na typie nie są bez blokady. Jeśli wartość wynosi 1, operacje mogą być zwolnić blokady i środowisko wykonawcze wyboru jest wymagana. Jeśli wartość jest równa 2, operacje są bez blokady. Można użyć funkcji `atomic_is_lock_free` pod kątem w czasie wykonywania operacji na typ bez blokady.  
  
 Dla każdego z typów całkowitych istnieje odpowiedni typ atomic nazwany zarządzanego obiektu typu całkowitego. Każdy `atomic_integral` typ ma ten sam zestaw funkcji Członkowskich jako odpowiednie tworzenia wystąpienia elementu `atomic<T>` i mogą zostać przekazane do żadnej funkcji atomic niebędący elementem członkowskim.  
  
|`atomic_integral` Typ|Typ całkowity|`atomic_is_lock_free` Makra|  
|----------------------------|-------------------|---------------------------------|  
|`atomic_char`|`char`|`ATOMIC_CHAR_LOCK_FREE`|  
|`atomic_schar`|`signed char`|`ATOMIC_CHAR_LOCK_FREE`|  
|`atomic_uchar`|`unsigned char`|`ATOMIC_CHAR_LOCK_FREE`|  
|`atomic_char16_t`|`char16_t`|`ATOMIC_CHAR16_T_LOCK_FREE`|  
|`atomic_char32_t`|`char32_t`|`ATOMIC_CHAR32_T_LOCK_FREE`|  
|`atomic_wchar_t`|`wchar_t`|`ATOMIC_WCHAR_T_LOCK_FREE`|  
|`atomic_short`|`short`|`ATOMIC_SHORT_LOCK_FREE`|  
|`atomic_ushort`|`unsigned short`|`ATOMIC_SHORT_LOCK_FREE`|  
|`atomic_int`|`int`|`ATOMIC_INT_LOCK_FREE`|  
|`atomic_uint`|`unsigned int`|`ATOMIC_INT_LOCK_FREE`|  
|`atomic_long`|`long`|`ATOMIC_LONG_LOCK_FREE`|  
|`atomic_ulong`|`unsigned long`|`ATOMIC_LONG_LOCK_FREE`|  
|`atomic_llong`|`long long`|`ATOMIC_LLONG_LOCK_FREE`|  
|`atomic_ullong`|`unsigned long long`|`ATOMIC_LLONG_LOCK_FREE`|  
  
 Nazwy elementów TypeDef istnieje dla specjalizacji szablonu atomic dla typów zdefiniowanych w nagłówku \<inttypes.h >.  
  
|Niepodzielne typu|Nazwa typu TypeDef|  
|-----------------|------------------|  
|`atomic_int8_t`|`atomic<int8_t>`|  
|`atomic_uint8_t`|`atomic<uint8_t>`|  
|`atomic_int16_t`|`atomic<int16_t>`|  
|`atomic_uint16_t`|`atomic<uint16_t>`|  
|`atomic_int32_t`|`atomic<int32_t>`|  
|`atomic_uint32_t`|`atomic<uint32_t>`|  
|`atomic_int64_t`|`atomic<int64_t>`|  
|`atomic_uint64_t`|`atomic<uint64_t>`|  
|`atomic_int_least8_t`|`atomic<int_least8_t>`|  
|`atomic_uint_least8_t`|`atomic<uint_least8_t>`|  
|`atomic_int_least16_t`|`atomic<int_least16_t>`|  
|`atomic_uint_least16_t`|`atomic<uint_least16_t>`|  
|`atomic_int_least32_t`|`atomic<int_least32_t>`|  
|`atomic_uint_least32_t`|`atomic<uint_least32_t>`|  
|`atomic_int_least64_t`|`atomic<int_least64_t>`|  
|`atomic_uint_least64_t`|`atomic<uint_least64_t>`|  
|`atomic_int_fast8_t`|`atomic<int_fast8_t>`|  
|`atomic_uint_fast8_t`|`atomic<uint_fast8_t>`|  
|`atomic_int_fast16_t`|`atomic<int_fast16_t>`|  
|`atomic_uint_fast16_`|`atomic<uint_fast16_t>`|  
|`atomic_int_fast32_t`|`atomic<int_fast32_t>`|  
|`atomic_uint_fast32_t`|`atomic<uint_fast32_t>`|  
|`atomic_int_fast64_t`|`atomic<int_fast64_t>`|  
|`atomic_uint_fast64_t`|`atomic<uint_fast64_t>`|  
|`atomic_intptr_t`|`atomic<intptr_t>`|  
|`atomic_uintptr_t`|`atomic<uintptr_t>`|  
|`atomic_size_t`|`atomic<size_t>`|  
|`atomic_ptrdiff_t`|`atomic<ptrdiff_t>`|  
|`atomic_intmax_t`|`atomic<intmax_t>`|  
|`atomic_uintmax_t`|`atomic<uintmax_t>`|  
  
## <a name="structs"></a>Struktury  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[atomic, struktura](../standard-library/atomic-structure.md)|Opis obiektu, który wykonuje niepodzielne operacje na przechowywanej wartości.|  
|[atomic_flag, struktura](../standard-library/atomic-flag-structure.md)|Opisuje obiekt, który automatycznie ustawia i usuwa `bool` flagi.|  
  
## <a name="enums"></a>Wyliczenia  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[memory_order Enum](../standard-library/atomic-enums.md#memory_order_enum)|Dostarcza nazw symbolicznych dla operacji synchronizacji w lokalizacji pamięci. Te operacje mają wpływ na sposób przydziały w jeden wątek stają się widoczne w innym.|  
  
## <a name="functions"></a>Funkcje  
 Na poniższej liście, funkcje, które nie kończą się `_explicit` ma semantykę odpowiadającego `_explicit`, z wyjątkiem tego, że mają one niejawne [memory_order](../standard-library/atomic-enums.md#memory_order_enum) argumenty `memory_order_seq_cst`.  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[atomic_compare_exchange_strong](../standard-library/atomic-functions.md#atomic_compare_exchange_strong)|Wykonuje *atomic porównania i exchange* operacji.|  
|[atomic_compare_exchange_strong_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_strong_explicit)|Wykonuje *atomic porównania i exchange* operacji.|  
|[atomic_compare_exchange_weak](../standard-library/atomic-functions.md#atomic_compare_exchange_weak)|Wykonuje *weak atomic porównania i exchange* operacji.|  
|[atomic_compare_exchange_weak_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_weak_explicit)|Wykonuje *weak atomic porównania i exchange* operacji.|  
|[atomic_exchange](../standard-library/atomic-functions.md#atomic_exchange)|Zastępuje przechowywanej wartości.|  
|[atomic_exchange_explicit](../standard-library/atomic-functions.md#atomic_exchange_explicit)|Zastępuje przechowywanej wartości.|  
|[atomic_fetch_add](../standard-library/atomic-functions.md#atomic_fetch_add)|Dodaje określoną wartość do istniejącej przechowywanej wartości.|  
|[atomic_fetch_add_explicit](../standard-library/atomic-functions.md#atomic_fetch_add_explicit)|Dodaje określoną wartość do istniejącej przechowywanej wartości.|  
|[atomic_fetch_and](../standard-library/atomic-functions.md#atomic_fetch_and)|Wykonuje bitowej `and` na określoną wartość i istniejąca przechowywana wartość.|  
|[atomic_fetch_and_explicit](../standard-library/atomic-functions.md#atomic_fetch_and_explicit)|Wykonuje bitowej `and` na określoną wartość i istniejąca przechowywana wartość.|  
|[atomic_fetch_or](../standard-library/atomic-functions.md#atomic_fetch_or)|Wykonuje bitowej `or` na określoną wartość i istniejąca przechowywana wartość.|  
|[atomic_fetch_or_explicit](../standard-library/atomic-functions.md#atomic_fetch_or_explicit)|Wykonuje bitowej `or` na określoną wartość i istniejąca przechowywana wartość.|  
|[atomic_fetch_sub](../standard-library/atomic-functions.md#atomic_fetch_sub)|Odejmuje określoną wartość z istniejąca przechowywana wartość.|  
|[atomic_fetch_sub_explicit](../standard-library/atomic-functions.md#atomic_fetch_sub_explicit)|Odejmuje określoną wartość z istniejąca przechowywana wartość.|  
|[atomic_fetch_xor](../standard-library/atomic-functions.md#atomic_fetch_xor)|Wykonuje bitowej `exclusive or` na określoną wartość i istniejąca przechowywana wartość.|  
|[atomic_fetch_xor_explicit](../standard-library/atomic-functions.md#atomic_fetch_xor_explicit)|Wykonuje bitowej `exclusive or` na określoną wartość i istniejąca przechowywana wartość.|  
|[atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear)|Ustawia flagę `atomic_flag` do obiektu `false`.|  
|[atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit)|Ustawia flagę `atomic_flag` do obiektu `false`.|  
|[atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set)|Ustawia flagę `atomic_flag` do obiektu `true`.|  
|[atomic_flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit)|Ustawia flagę `atomic_flag` do obiektu `true`.|  
|[atomic_init](../standard-library/atomic-functions.md#atomic_init)|Ustawia wartość przechowywana w `atomic` obiektu.|  
|[atomic_is_lock_free](../standard-library/atomic-functions.md#atomic_is_lock_free)|Określa, czy są niepodzielne operacje na określony obiekt bez blokady.|  
|[atomic_load](../standard-library/atomic-functions.md#atomic_load)|Automatycznie pobiera wartość.|  
|[atomic_load_explicit](../standard-library/atomic-functions.md#atomic_load_explicit)|Automatycznie pobiera wartość.|  
|[atomic_signal_fence](../standard-library/atomic-functions.md#atomic_signal_fence)|Zachowuje się jak *ogrodzenia* który ustanawia pamięci kolejności, wymagania dotyczące ogrodzenia w wywołaniu wątku, który ma obsługę sygnału wykonywanych w tym samym wątku.|  
|[atomic_store](../standard-library/atomic-functions.md#atomic_store)|Automatycznie zapisuje wartość.|  
|[atomic_store_explicit](../standard-library/atomic-functions.md#atomic_store_explicit)|Automatycznie zapisuje wartość.|  
|[atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence)|Zachowuje się jak *ogrodzenia* który określa kolejność wymagania względem innych ogrodzenia pamięci.|  
|[kill_dependency](../standard-library/atomic-functions.md#kill_dependency)|Dzieli łańcuch zależności możliwe.|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)





