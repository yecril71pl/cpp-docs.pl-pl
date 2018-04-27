---
title: '&lt;nowe&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- <new>
dev_langs:
- C++
helpviewer_keywords:
- new header
ms.assetid: 218e2a15-34e8-4ef3-9122-1e90eccf8559
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 17a72100dbfb51fae9085e3900cd180bde0a31be
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ltnewgt"></a>&lt;new&gt;

Definiuje kilka typy i funkcje tego formantu alokacji i zwalnianie magazynu pod kontrolą programu. Definiuje również składniki raportowania błędów zarządzania magazynu.

## <a name="syntax"></a>Składnia

```cpp
#include <new>

```

## <a name="remarks"></a>Uwagi

Niektóre funkcje zadeklarowany w tym nagłówkiem są wymienne. Implementacja udostępnia domyślną wersję, w których zachowanie jest opisane w tym dokumencie. Program można jednak zdefiniować funkcja o tej samej sygnaturze, aby zamienić wersję domyślną w czasie łącza. Wersja zastąpienie musi spełniać wymagania opisane w tym dokumencie.

### <a name="objects"></a>Obiekty

|||
|-|-|
|[nothrow](../standard-library/new-functions.md#nothrow)|Udostępnia obiekt ma być używany jako argument `nothrow` wersji **nowe** i **usunąć**.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[new_handler](../standard-library/new-typedefs.md#new_handler)|Typ, który wskazuje na funkcję odpowiednie do użycia jako nowy program obsługi.|

### <a name="functions"></a>Funkcje

|Funkcja|Opis|
|-|-|
|[set_new_handler](../standard-library/new-functions.md#set_new_handler)|Instalowanie funkcji użytkownika, który jest wywoływany, gdy nowy może przydzielić pamięci nie powiedzie się.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[Usuwanie operatora](../standard-library/new-operators.md#op_delete)|Funkcja wywoływana przez wyrażenie usunięcia, należy cofnąć magazynu dla poszczególnych obiektów.|
|[Usuwanie operatora&#91;&#93;](../standard-library/new-operators.md#op_delete_arr)|Funkcja wywoływana przez wyrażenie usuwania można cofnąć alokacji pamięci masowej dla tablicy obiektów.|
|[nowy operator](../standard-library/new-operators.md#op_new)|Funkcja wywoływana przez nowe wyrażenie, aby przydzielić magazyn dla poszczególnych obiektów.|
|[nowy operator&#91;&#93;](../standard-library/new-operators.md#op_new_arr)|Funkcja wywoływana przez nowe wyrażenie, aby przydzielić magazyn na tablicę obiektów.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[bad_alloc, klasa](../standard-library/bad-alloc-class.md)|Klasa opisuje wyjątek, aby wskazać, że żądanie alokacji nie powiodła się.|
|[nothrow_t — klasa](../standard-library/nothrow-t-structure.md)|Klasa jest używana jako parametru funkcji operatora nowe do wskazują, że funkcja powinna zwrócić pustego wskaźnika Zgłoś błąd alokacji zamiast Zgłoś wyjątek.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
