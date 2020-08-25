---
title: '&lt;new&gt;'
ms.date: 11/04/2016
f1_keywords:
- <new>
helpviewer_keywords:
- new header
ms.assetid: 218e2a15-34e8-4ef3-9122-1e90eccf8559
ms.openlocfilehash: 0fe2d0e57c0746f25187028b85157d66ee736ca4
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836429"
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

|Nazwa|Opis|
|-|-|
|[nothrow](../standard-library/new-functions.md#nothrow)|Dostarcza obiekt, który ma być używany jako argument dla **`nothrow`** wersji **`new`** i **`delete`** .|

### <a name="typedefs"></a>Typedefs

|Nazwa|Opis|
|-|-|
|[new_handler](../standard-library/new-typedefs.md#new_handler)|Typ, który wskazuje funkcję odpowiednią do użycia jako nowy program obsługi.|
|[hardware_constructive_interference_size](../standard-library/new-typedefs.md#hardware_destructive_interference_size)||
|[hardware_destructive_interference_size](../standard-library/new-typedefs.md#hardware_destructive_interference_size)||

### <a name="functions"></a>Functions

|Nazwa|Opis|
|-|-|
|[get_new_handler](../standard-library/new-functions.md#get_new_handler)||
|[brudn](../standard-library/new-functions.md#launder)||
|[set_new_handler](../standard-library/new-functions.md#set_new_handler)|Instaluje funkcję użytkownika, która jest wywoływana, gdy nowa operacja kończy się niepowodzeniem w trakcie próby przydzielenia pamięci.|

### <a name="operators"></a>Operatory

|Nazwa|Opis|
|-|-|
|[Usuwanie operatora](../standard-library/new-operators.md#op_delete)|Funkcja wywołana przez wyrażenie delete do dealokacji magazynu dla poszczególnych obiektów.|
|[&#91;&#93;usuwania operatora ](../standard-library/new-operators.md#op_delete_arr)|Funkcja wywołana przez wyrażenie delete do dealokacji magazynu dla tablicy obiektów.|
|[Nowy operator](../standard-library/new-operators.md#op_new)|Funkcja wywołana przez nowe wyrażenie do przydzielania pamięci dla pojedynczych obiektów.|
|[Nowy&#91;&#93;operatora ](../standard-library/new-operators.md#op_new_arr)|Funkcja wywołana przez nowe wyrażenie do przydzielenia magazynu dla tablicy obiektów.|

### <a name="enums"></a>Wyliczenia

|Nazwa|Opis|
|-|-|
|[align_val_t](../standard-library/new-operators.md#op_align_val_t)||

### <a name="classes"></a>Klasy

|Nazwa|Opis|
|-|-|
|[Klasa bad_alloc](../standard-library/bad-alloc-class.md)|Klasa zawiera opis zgłoszonego wyjątku, aby wskazać, że żądanie alokacji nie powiodło się.|
|[Klasa bad_array_new_length](../standard-library/bad-array-new-length.md)||
|[Klasa nothrow_t](../standard-library/nothrow-t-structure.md)|Klasa jest używana jako parametr funkcji dla operatora new, aby wskazać, że funkcja powinna zwrócić wskaźnik o wartości null, aby zgłosić błąd alokacji, zamiast zgłosić wyjątek.|

## <a name="see-also"></a>Zobacz też

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
