---
title: '&lt;new&gt;'
ms.date: 11/04/2016
f1_keywords:
- <new>
helpviewer_keywords:
- new header
ms.assetid: 218e2a15-34e8-4ef3-9122-1e90eccf8559
ms.openlocfilehash: b6f1cc45f9666fc0fbd2332ac7bb7e539ec77cd3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223652"
---
# <a name="ltnewgt"></a>&lt;new&gt;

Definiuje kilka typów i funkcji w tej kontrolki alokacji i zwalnianiem pamięci pod kontrolą programu. Definiuje również składniki raportowania błędów zarządzania magazynu.

## <a name="syntax"></a>Składnia

```cpp
#include <new>
```

## <a name="remarks"></a>Uwagi

Niektóre funkcje zadeklarowane w tym nagłówku są wymienne. Implementacja dostarcza domyślnej wersji, którego zachowanie jest opisane w tym dokumencie. Program można jednak zdefiniować funkcję z tym samym podpisie w celu zastąpienia domyślnej wersji w czasie połączenia. Wersja zastąpienie musi spełniać wymagania opisane w tym dokumencie.

### <a name="objects"></a>Obiekty

|||
|-|-|
|[nothrow](../standard-library/new-functions.md#nothrow)|Zapewnia obiekt ma być używany jako argument dla **nothrow** wersje **nowe** i **Usuń**.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[new_handler](../standard-library/new-typedefs.md#new_handler)|Typ, który wskazuje do funkcji odpowiedni do użytku jako nowy program obsługi.|

### <a name="functions"></a>Funkcje

|Funkcja|Opis|
|-|-|
|[set_new_handler](../standard-library/new-functions.md#set_new_handler)|Instaluje funkcję użytkownika, która jest wywoływana, gdy nowy może przydzielić pamięci nie powiedzie się.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[Usuwanie operatora](../standard-library/new-operators.md#op_delete)|Funkcja wywoływana przez wyrażenie delete, aby cofnięcie przydziału magazynu dla poszczególnych obiektów.|
|[Usuwanie operatora&#91;&#93;](../standard-library/new-operators.md#op_delete_arr)|Funkcja wywoływana przez wyrażenie usunięcia można cofnąć alokacji pamięci masowej na tablicę obiektów.|
|[nowy operator](../standard-library/new-operators.md#op_new)|Funkcja wywoływana przez nowe wyrażenie do przydzielania pamięci dla poszczególnych obiektów.|
|[nowy operator&#91;&#93;](../standard-library/new-operators.md#op_new_arr)|Funkcja wywoływana przez nowe wyrażenie do przydzielania pamięci dla tablicy obiektów.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[bad_alloc, klasa](../standard-library/bad-alloc-class.md)|Klasa opisuje wyjątek generowany, aby wskazać, że żądanie alokacji nie powiodła się.|
|[nothrow_t — klasa](../standard-library/nothrow-t-structure.md)|Klasa jest używana jako parametru funkcji, operatorów nowych do wskazania, że funkcja powinna zwrócić wskaźnik o wartości null do raportu wystąpił błąd alokacji, a nie zgłasza wyjątku.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
