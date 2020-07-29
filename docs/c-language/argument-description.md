---
title: Opis argumentu
ms.date: 11/04/2016
helpviewer_keywords:
- envp argument
- main function, syntax
- arguments [C++], for main function
- argv argument
- argc argument
ms.assetid: 91c2cbe3-9aca-4277-afa1-6137eb8fb704
ms.openlocfilehash: dd973c96c9056f6156976698dfc3695b00ebbbb7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87200871"
---
# <a name="argument-description"></a>Opis argumentu

`argc`Parametr w funkcjach **Main** i **wmain** jest liczbą całkowitą określającą liczbę argumentów, które są przekazane do programu z wiersza polecenia. Ponieważ nazwa programu jest traktowana jako argument, wartość jest równa co `argc` najmniej jednej.

## <a name="remarks"></a>Uwagi

`argv`Parametr jest tablicą wskaźników do ciągów zakończonych znakiem null reprezentujących argumenty programu. Każdy element tablicy wskazuje reprezentację argumentu przekazaną do **Main** (lub **wmain**). (Aby uzyskać informacje na temat tablic, zobacz [deklaracje tablicowe](../c-language/array-declarations.md)). `argv`Parametr może być zadeklarowany jako tablica wskaźników do typu **`char`** ( `char *argv[]` ) lub jako wskaźnik do wskaźników do typu **`char`** ( `char **argv` ). Dla **wmain** `argv` parametr może być zadeklarowany jako tablica wskaźników do typu **`wchar_t`** ( `wchar_t *argv[]` ) lub jako wskaźnik do wskaźników do typu **`wchar_t`** ( `wchar_t **argv` ).

Zgodnie z Konwencją, `argv` **[0]** jest poleceniem, z którym wywoływany jest program.  Istnieje jednak możliwość duplikowania procesu przy użyciu metody [CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw) , a jeśli używasz zarówno pierwszego, jak i drugiego argumentu ( `lpApplicationName` i `lpCommandLine` ), `argv` **[0]** nie może być nazwą pliku wykonywalnego; Użyj [Funkcja GetModuleFileName](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) , aby pobrać nazwę pliku wykonywalnego.

Ostatni wskaźnik ( `argv[argc]` ) ma **wartość null**. (Zobacz [getenv](../c-runtime-library/reference/getenv-wgetenv.md) w *dokumentacji środowiska wykonawczego* , aby uzyskać alternatywną metodę uzyskiwania informacji o zmiennych środowiskowych).

**Specyficzne dla firmy Microsoft**

`envp`Parametr jest wskaźnikiem do tablicy ciągów zakończonych wartością null, które reprezentują wartości ustawione w zmiennych środowiskowych użytkownika. `envp`Parametr może być zadeklarowany jako tablica wskaźników do **`char`** ( `char *envp[]` ) lub jako wskaźnik do wskaźników **`char`** ( `char **envp` ). W funkcji **wmain** `envp` parametr może być zadeklarowany jako tablica wskaźników do **`wchar_t`** ( `wchar_t *envp[]` ) lub jako wskaźnik do wskaźników **`wchar_t`** ( `wchar_t **envp` ). Koniec tablicy jest wskazywany przez wskaźnik o **wartości null** \* . Należy zauważyć, że blok środowiska przeszedł do **Main** lub **wmain** jest kopią "zamrożoną" bieżącego środowiska. Jeśli później zmienisz środowisko za pośrednictwem wywołania do _**putenv** lub `_wputenv` , bieżące środowisko (zwracane przez `getenv` / `_wgetenv` i `_environ` `_wenviron` zmienne or) ulegnie zmianie, ale blok wskazywany przez `envp` nie zmieni się. `envp`Parametr jest zgodny ze standardem ANSI w C, ale nie w języku C++.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcja Main i wykonywanie programu](../c-language/main-function-and-program-execution.md)
