---
title: '&lt;new&gt;'
ms.date: 11/04/2016
f1_keywords:
- <new>
helpviewer_keywords:
- new header
ms.assetid: 218e2a15-34e8-4ef3-9122-1e90eccf8559
ms.openlocfilehash: 2a35a7b4d9581a11d889f3e66d0179c553c4fc25
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212166"
---
# <a name="ltnewgt"></a>&lt;new&gt;

Definiuje kilka typów i funkcji kontrolujących alokację i zwalnianie magazynu w ramach kontroli programu. Definiuje także składniki służące do raportowania błędów zarządzania magazynem.

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<new>

**Przestrzeń nazw:** std

## <a name="remarks"></a>Uwagi

Niektóre funkcje zadeklarowane w tym nagłówku są wymienne. Implementacja dostarcza wersję domyślną, której zachowanie zostało opisane w tym dokumencie. Program może jednak zdefiniować funkcję o tym samym podpisie, aby zastąpić domyślną wersję w czasie łącza. Wersja zastępująca musi spełniać wymagania opisane w tym dokumencie.

## <a name="members"></a>Elementy członkowskie

### <a name="objects"></a>Obiekty

|||
|-|-|
|[nothrow](../standard-library/new-functions.md#nothrow)|Dostarcza obiekt, który ma być używany jako argument dla **`nothrow`** wersji **`new`** i **`delete`** .|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[new_handler](../standard-library/new-typedefs.md#new_handler)|Typ, który wskazuje funkcję odpowiednią do użycia jako nowy program obsługi.|
|[hardware_constructive_interference_size](../standard-library/new-typedefs.md#hardware_destructive_interference_size)||
|[hardware_destructive_interference_size](../standard-library/new-typedefs.md#hardware_destructive_interference_size)||

### <a name="functions"></a>Funkcje

|||
|-|-|
|[get_new_handler](../standard-library/new-functions.md#get_new_handler)||
|[brudn](../standard-library/new-functions.md#launder)||
|[set_new_handler](../standard-library/new-functions.md#set_new_handler)|Instaluje funkcję użytkownika, która jest wywoływana, gdy nowa operacja kończy się niepowodzeniem w trakcie próby przydzielenia pamięci.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[Usuwanie operatora](../standard-library/new-operators.md#op_delete)|Funkcja wywołana przez wyrażenie delete do dealokacji magazynu dla poszczególnych obiektów.|
|[&#91;&#93;usuwania operatora](../standard-library/new-operators.md#op_delete_arr)|Funkcja wywołana przez wyrażenie delete do dealokacji magazynu dla tablicy obiektów.|
|[Nowy operator](../standard-library/new-operators.md#op_new)|Funkcja wywołana przez nowe wyrażenie do przydzielania pamięci dla pojedynczych obiektów.|
|[Nowy&#91;&#93;operatora](../standard-library/new-operators.md#op_new_arr)|Funkcja wywołana przez nowe wyrażenie do przydzielenia magazynu dla tablicy obiektów.|

### <a name="enums"></a>Wyliczenia

|||
|-|-|
|[align_val_t](../standard-library/new-operators.md#op_align_val_t)||

### <a name="classes"></a>Klasy

|||
|-|-|
|[Klasa bad_alloc](../standard-library/bad-alloc-class.md)|Klasa zawiera opis zgłoszonego wyjątku, aby wskazać, że żądanie alokacji nie powiodło się.|
|[Klasa bad_array_new_length](../standard-library/bad-array-new-length.md)||
|[Klasa nothrow_t](../standard-library/nothrow-t-structure.md)|Klasa jest używana jako parametr funkcji dla operatora new, aby wskazać, że funkcja powinna zwrócić wskaźnik o wartości null, aby zgłosić błąd alokacji, zamiast zgłosić wyjątek.|

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
