---
title: '&lt;Atomic&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 54ea69a53204de2d304340ed042b3ba028dd404c
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38966644"
---
# <a name="ltatomicgt"></a>&lt;atomic&gt;

Definiuje klasy i szablonu klasy służące do tworzenia typów, które obsługują niepodzielnych operacji.

## <a name="syntax"></a>Składnia

```cpp
#include <atomic>
```

## <a name="remarks"></a>Uwagi

> [!NOTE]
> W kodzie, który jest kompilowany przy użyciu **/CLR**, tego pliku nagłówkowego jest zablokowany.

Operacją niepodzielną ma dwie właściwości klucza, które ułatwiają poprawnie zaznaczać obiektu bez używania blokad mutex za pomocą wielu wątków.

- Ponieważ niepodzielną operacją niepodzielną, drugą operację niepodzielną do tego samego obiektu z innego wątku można uzyskać stanu obiektu tylko przed lub po pierwszą operacją niepodzielną.

- Na podstawie jego [memory_order](../standard-library/atomic-enums.md#memory_order_enum) argument operacją niepodzielną ustanawia porządkowanie wymagań w zakresie widoczność efektów innych operacji atomowych wykonywanych w tym samym wątku. W związku z tym powstrzymuje optymalizacje kompilatora, które naruszają szeregowania wymagania.

Na niektórych platformach go może nie być możliwe do wydajnego implementowania operacji niepodzielnych w przypadku niektórych typów bez użycia `mutex` blokad. Typ niepodzielny *wolne od blokady* Jeśli żadne operacje niepodzielne tego typu nie używają blokady.

**C ++ 11**: W procedurach obsługi sygnału można wykonywać niepodzielne operacje na obiekcie `obj` Jeśli `obj.is_lock_free()` lub `atomic_is_lock_free(x)` mają wartość true.

Klasa [atomic_flag](../standard-library/atomic-flag-structure.md) zapewnia minimalne typ niepodzielny, zawierający **bool** flagi. Jej operacje są zawsze wolne od blokady.

Klasa szablonu `atomic<T>` przechowuje obiekt typu argumentu `T` i zapewnia atomic dostęp do tego przechowywanej wartości. Można utworzyć za pomocą dowolnego typu, który można skopiować przy użyciu [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) i sprawdzane pod kątem równości, za pomocą [memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md). W szczególności umożliwia ona z typami zdefiniowanymi przez użytkownika, które spełniają te wymagania i w wielu przypadkach z typów zmiennoprzecinkowych.

Szablon ma również zbiór specjalizacje w przypadku typów całkowitych i częściowej specjalizacji dla wskaźników. Te specjalizacje zapewniają dodatkowe operacje, które nie są dostępne za pośrednictwem szablonu podstawowego.

## <a name="pointer-specializations"></a>Wskaźnik specjalizacji

`atomic<T *>` Specjalizacjami częściowymi mają zastosowanie do wszystkich typów wskaźnika. Zapewniają one metody arytmetyka wskaźnika.

## <a name="integral-specializations"></a>Integralne specjalizacje

`atomic<integral>` Specjalizacje mają zastosowanie do wszystkich typów całkowitych. Zapewniają one dodatkowe operacje, które nie są dostępne za pośrednictwem szablonu podstawowego.

Każdy `atomic<integral>` typ ma odpowiednie makro, które można używać w `if directive` do określenia w czasie kompilacji, czy operacje tego typu są wolne od blokady. Jeśli wartość makra wynosi zero, operacje typu nie są wolne od blokady. Jeśli wartość wynosi 1, operacji może być wolne od blokady i środowisko uruchomieniowe wyboru jest wymagana. Jeśli wartość jest równa 2, operacje są wolne od blokady. Można użyć funkcji `atomic_is_lock_free` pod kątem w czasie wykonywania operacji na typie wolne od blokady.

Dla każdego z typów całkowitych ma odpowiedni typ niepodzielny nazwane zarządzanego obiektu typu całkowitego. Każdy `atomic_integral` typ ma ten sam zestaw funkcji elementów członkowskich jako odpowiedniego wystąpienia `atomic<T>` i mogą być przekazywane do dowolnego atomic funkcje nieczłonkowskie.

|`atomic_integral` Typ|Typ całkowity|`atomic_is_lock_free` — Makro|
|----------------------------|-------------------|---------------------------------|
|`atomic_char`|**char**|ATOMIC_CHAR_LOCK_FREE|
|`atomic_schar`|**podpisany char**|ATOMIC_CHAR_LOCK_FREE|
|`atomic_uchar`|**unsigned char**|ATOMIC_CHAR_LOCK_FREE|
|`atomic_char16_t`|`char16_t`|ATOMIC_CHAR16_T_LOCK_FREE|
|`atomic_char32_t`|`char32_t`|ATOMIC_CHAR32_T_LOCK_FREE|
|`atomic_wchar_t`|**wchar_t**|ATOMIC_WCHAR_T_LOCK_FREE|
|`atomic_short`|**short**|ATOMIC_SHORT_LOCK_FREE|
|`atomic_ushort`|**short bez znaku**|ATOMIC_SHORT_LOCK_FREE|
|`atomic_int`|**int**|ATOMIC_INT_LOCK_FREE|
|`atomic_uint`|**unsigned int**|ATOMIC_INT_LOCK_FREE|
|`atomic_long`|**long**|ATOMIC_LONG_LOCK_FREE|
|`atomic_ulong`|**unsigned long**|ATOMIC_LONG_LOCK_FREE|
|`atomic_llong`|**długi długi**|ATOMIC_LLONG_LOCK_FREE|
|`atomic_ullong`|**Nieoznaczony długi długi**|ATOMIC_LLONG_LOCK_FREE|

Nazwy elementów TypeDef istnieje dla specjalizacji szablonu atomic dla niektórych typów, które są zdefiniowane w nagłówku \<inttypes.h >.

|Typ niepodzielny|Nazwa TypeDef|
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
|[atomic, struktura](../standard-library/atomic-structure.md)|Opisuje obiekt, który wykonuje niepodzielne operacje na przechowywanej wartości.|
|[atomic_flag, struktura](../standard-library/atomic-flag-structure.md)|Opisuje obiekt, który niepodzielnie Ustawia lub usuwa **bool** flagi.|

## <a name="enums"></a>Wyliczenia

|Nazwa|Opis|
|----------|-----------------|
|[memory_order Enum](../standard-library/atomic-enums.md#memory_order_enum)|Dostarcza symbolicznych nazw dla operacji synchronizacji w lokalizacji pamięci. Operacje te wpływają na jak przydziały w jednym wątku stają się widoczne w innym.|

## <a name="functions"></a>Funkcje

Na liście poniżej, funkcje, które nie kończą się na `_explicit` ma semantykę odpowiadającego `_explicit`, chyba że mają niejawny [memory_order](../standard-library/atomic-enums.md#memory_order_enum) argumenty `memory_order_seq_cst`.

|Nazwa|Opis|
|----------|-----------------|
|[atomic_compare_exchange_strong](../standard-library/atomic-functions.md#atomic_compare_exchange_strong)|Wykonuje *porównanie atomowe i wymianę* operacji.|
|[atomic_compare_exchange_strong_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_strong_explicit)|Wykonuje *porównanie atomowe i wymianę* operacji.|
|[atomic_compare_exchange_weak](../standard-library/atomic-functions.md#atomic_compare_exchange_weak)|Wykonuje *weak atomic porównania i wymiany* operacji.|
|[atomic_compare_exchange_weak_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_weak_explicit)|Wykonuje *weak atomic porównania i wymiany* operacji.|
|[atomic_exchange](../standard-library/atomic-functions.md#atomic_exchange)|Zastępuje przechowywanej wartości.|
|[atomic_exchange_explicit](../standard-library/atomic-functions.md#atomic_exchange_explicit)|Zastępuje przechowywanej wartości.|
|[atomic_fetch_add](../standard-library/atomic-functions.md#atomic_fetch_add)|Dodaje określoną wartość do istniejącej wartości przechowywanej.|
|[atomic_fetch_add_explicit](../standard-library/atomic-functions.md#atomic_fetch_add_explicit)|Dodaje określoną wartość do istniejącej wartości przechowywanej.|
|[atomic_fetch_and](../standard-library/atomic-functions.md#atomic_fetch_and)|Wykonuje bitową operację `and` na określoną wartość i istniejącej wartości przechowywanej.|
|[atomic_fetch_and_explicit](../standard-library/atomic-functions.md#atomic_fetch_and_explicit)|Wykonuje bitową operację `and` na określoną wartość i istniejącej wartości przechowywanej.|
|[atomic_fetch_or](../standard-library/atomic-functions.md#atomic_fetch_or)|Wykonuje bitową operację `or` na określoną wartość i istniejącej wartości przechowywanej.|
|[atomic_fetch_or_explicit](../standard-library/atomic-functions.md#atomic_fetch_or_explicit)|Wykonuje bitową operację `or` na określoną wartość i istniejącej wartości przechowywanej.|
|[atomic_fetch_sub](../standard-library/atomic-functions.md#atomic_fetch_sub)|Odejmuje określoną wartość z istniejącej wartości przechowywanej.|
|[atomic_fetch_sub_explicit](../standard-library/atomic-functions.md#atomic_fetch_sub_explicit)|Odejmuje określoną wartość z istniejącej wartości przechowywanej.|
|[atomic_fetch_xor](../standard-library/atomic-functions.md#atomic_fetch_xor)|Wykonuje bitową operację `exclusive or` na określoną wartość i istniejącej wartości przechowywanej.|
|[atomic_fetch_xor_explicit](../standard-library/atomic-functions.md#atomic_fetch_xor_explicit)|Wykonuje bitową operację `exclusive or` na określoną wartość i istniejącej wartości przechowywanej.|
|[atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear)|Ustawia flagę `atomic_flag` obiekt **false**.|
|[atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit)|Ustawia flagę `atomic_flag` obiekt **false**.|
|[atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set)|Ustawia flagę `atomic_flag` obiekt **true**.|
|[atomic_flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit)|Ustawia flagę `atomic_flag` obiekt **true**.|
|[atomic_init](../standard-library/atomic-functions.md#atomic_init)|Ustawia wartość przechowywaną w `atomic` obiektu.|
|[atomic_is_lock_free](../standard-library/atomic-functions.md#atomic_is_lock_free)|Określa, czy niepodzielne operacje na określony obiekt są wolne od blokady.|
|[atomic_load —](../standard-library/atomic-functions.md#atomic_load)|Niepodzielnie pobiera wartość.|
|[atomic_load_explicit](../standard-library/atomic-functions.md#atomic_load_explicit)|Niepodzielnie pobiera wartość.|
|[atomic_signal_fence](../standard-library/atomic-functions.md#atomic_signal_fence)|Działa jako *horyzont* który ustanawia pamięci zamawiania, wymagania dotyczące zaporami wywołującymi wywołania wątku, który ma procedurach obsługi sygnału wykonywane w tym samym wątku.|
|[atomic_store](../standard-library/atomic-functions.md#atomic_store)|Niepodzielne przechowuje wartość.|
|[atomic_store_explicit](../standard-library/atomic-functions.md#atomic_store_explicit)|Niepodzielne przechowuje wartość.|
|[atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence)|Działa jako *horyzont* który ustanawia pamięci zamawiania wymagań dotyczących innymi zaporami wywołującymi.|
|[kill_dependency](../standard-library/atomic-functions.md#kill_dependency)|Przerywa łańcuch zależności możliwe.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
