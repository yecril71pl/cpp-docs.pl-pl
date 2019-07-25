---
title: '&lt;new&gt;'
ms.date: 11/04/2016
f1_keywords:
- <new>
helpviewer_keywords:
- new header
ms.assetid: 218e2a15-34e8-4ef3-9122-1e90eccf8559
ms.openlocfilehash: 6155a89c9cbba67ce27253aa64ff70ca7871e748
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457688"
---
# <a name="ltnewgt"></a>&lt;new&gt;

Definiuje kilka typów i funkcji kontrolujących alokację i zwalnianie magazynu w ramach kontroli programu. Definiuje także składniki służące do raportowania błędów zarządzania magazynem.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<nowe >

**Przestrzeń nazw:** std

## <a name="remarks"></a>Uwagi

Niektóre funkcje zadeklarowane w tym nagłówku są wymienne. Implementacja dostarcza wersję domyślną, której zachowanie zostało opisane w tym dokumencie. Program może jednak zdefiniować funkcję o tym samym podpisie, aby zastąpić domyślną wersję w czasie łącza. Wersja zastępująca musi spełniać wymagania opisane w tym dokumencie.

## <a name="members"></a>Elementy członkowskie

### <a name="objects"></a>Obiekty

|||
|-|-|
|[nothrow](../standard-library/new-functions.md#nothrow)|Zawiera obiekt, który ma być używany jako argument dla wersji  "nothrow" **nowych** i **usuniętych**.|

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
|[Usuwanie operatora&#91;&#93;](../standard-library/new-operators.md#op_delete_arr)|Funkcja wywołana przez wyrażenie delete do dealokacji magazynu dla tablicy obiektów.|
|[Nowy operator](../standard-library/new-operators.md#op_new)|Funkcja wywołana przez nowe wyrażenie do przydzielania pamięci dla pojedynczych obiektów.|
|[Nowy operator&#91;&#93;](../standard-library/new-operators.md#op_new_arr)|Funkcja wywołana przez nowe wyrażenie do przydzielenia magazynu dla tablicy obiektów.|

### <a name="enums"></a>Wyliczenia

|||
|-|-|
|[align_val_t](../standard-library/new-operators.md#op_align_val_t)||

### <a name="classes"></a>Klasy

|||
|-|-|
|[bad_alloc, klasa](../standard-library/bad-alloc-class.md)|Klasa zawiera opis zgłoszonego wyjątku, aby wskazać, że żądanie alokacji nie powiodło się.|
|[Klasa bad_array_new_length](../standard-library/bad-array-new-length.md)||
|[Klasa nothrow_t](../standard-library/nothrow-t-structure.md)|Klasa jest używana jako parametr funkcji dla operatora new, aby wskazać, że funkcja powinna zwrócić wskaźnik o wartości null, aby zgłosić błąd alokacji, zamiast zgłosić wyjątek.|

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
