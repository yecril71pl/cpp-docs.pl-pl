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
ms.openlocfilehash: 71301bd5eedf2806e97b8d24d95beaf2843427ad
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148507"
---
# <a name="argument-description"></a>Opis argumentu

`argc` Parametru w **głównego** i **wmain** funkcji jest liczbą całkowitą, określając, ile argumentów są przekazywane do programu z poziomu wiersza polecenia. Ponieważ nazwa programu jest uznawany za argument, a wartość `argc` co najmniej jeden.

## <a name="remarks"></a>Uwagi

`argv` Parametr jest tablicą wskaźników do ciągów znaków zakończony znakiem null, reprezentujący argumenty programu. Każdy element punktów tablicy na ciąg reprezentujący argument przekazany do **głównego** (lub **wmain**). (Aby uzyskać informacje na temat tablic, zobacz [deklaracje tablicy](../c-language/array-declarations.md).) `argv` Parametru może być zadeklarowana jako tablica wskaźników do typu `char` (`char *argv[]`) lub jako wskaźnik do wskaźników do typu `char` (`char **argv`). Aby uzyskać **wmain**, `argv` parametru może być zadeklarowana jako tablica wskaźników do typu `wchar_t` (`wchar_t *argv[]`) lub jako wskaźnik do wskaźników do typu `wchar_t` (`wchar_t **argv`).

Zgodnie z Konwencją `argv` **[0]** jest poleceniem, z którym wywoływany jest program.  Jednak jest możliwe, aby utworzyć proces przy użyciu [CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa) i jeśli korzystasz z pierwszego i drugiego argumentu (`lpApplicationName` i `lpCommandLine`), `argv` **[0]** może nie być Nazwa pliku wykonywalnego; Użyj [Funkcja GetModuleFileName](/windows/desktop/api/libloaderapi/nf-libloaderapi-getmodulefilenamea) można pobrać nazwy pliku wykonywalnego.

Ostatnie wskaźnika (`argv[argc]`) jest **NULL**. (Zobacz [getenv](../c-runtime-library/reference/getenv-wgetenv.md) w *odwołanie do biblioteki wykonawczej* dla alternatywną metodę w celu uzyskania informacji o zmiennej środowiska.)

**Microsoft Specific**

`envp` Parametr jest wskaźnikiem do tablicy zakończony znakiem null ciągi znaków reprezentujące wartości zmiennych środowiskowych użytkownika. `envp` Parametru mogą być deklarowane jako tablicę wskaźników do `char` (`char *envp[]`) lub jako wskaźnik do wskaźników do `char` (`char **envp`). W **wmain** funkcji `envp` parametru mogą być deklarowane jako tablicę wskaźników do `wchar_t` (`wchar_t *envp[]`) lub jako wskaźnik do wskaźników do `wchar_t` (`wchar_t **envp`). Końca tablicy jest wskazywana przez **NULL** \*wskaźnika. Należy zauważyć, że blok środowiska przekazany do **głównego** lub **wmain** jest "zamrożoną" kopią bieżącego środowiska. Jeśli następnie zmienisz środowisko przez wywołanie _**putenv** lub `_wputenv`, bieżące środowisko (zwrócone przez `getenv` / `_wgetenv` i `_environ` lub `_wenviron` zmienne) ulegnie zmianie, ale blok wskazywany przez `envp` nie ulegnie zmianie. `envp` Parametr jest zgodny w języku C, ale nie w języku C++ ze standardem ANSI.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcja main i wykonywanie programu](../c-language/main-function-and-program-execution.md)
