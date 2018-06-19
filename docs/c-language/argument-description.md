---
title: Opis argumentu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- envp argument
- main function, syntax
- arguments [C++], for main function
- argv argument
- argc argument
ms.assetid: 91c2cbe3-9aca-4277-afa1-6137eb8fb704
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 615fc3a68153386174ce0477ee5c946f50f37d90
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32385087"
---
# <a name="argument-description"></a>Opis argumentu
`argc` Parametru w **głównego** i **wmain** funkcji jest na liczbę całkowitą określającą liczbę argumentów są przekazywane do programu z wiersza polecenia. Ponieważ nazwa programu jest traktowane jako argument, a wartość `argc` co najmniej jeden.  
  
## <a name="remarks"></a>Uwagi  
 `argv` Parametr ma tablicę wskaźników do zerem ciągów reprezentujących argumenty programu. Każdy element tablicy punktami reprezentację ciągu argument przekazany do **głównego** (lub **wmain**). (Aby uzyskać informacje dotyczące tablic, zobacz [deklaracje tablicy](../c-language/array-declarations.md).) `argv` Parametru mogą być deklarowane jako tablicy wskaźników do typu `char` (`char *argv[]`) lub jako wskaźnik do wskaźników do typu `char` (`char **argv`). Aby uzyskać **wmain**, `argv` parametru mogą być deklarowane jako tablicy wskaźników do typu `wchar_t` (`wchar_t *argv[]`) lub jako wskaźnik do wskaźników do typu `wchar_t` (`wchar_t **argv`).  
  
 Według konwencji `argv` **[0]** polecenia, z którym program jest wywoływany.  Jednak jest możliwe zduplikować procesu przy użyciu [CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms682425) i użycie pierwszy i drugi argument (`lpApplicationName` i `lpCommandLine`), `argv` **[0]** nie może być Nazwa pliku wykonywalnego; Użyj [Funkcja GetModuleFileName](http://msdn.microsoft.com/library/windows/desktop/ms683197) można pobrać nazwy pliku wykonywalnego.  
  
 Ostatni wskaźnika (`argv[argc]`) jest **NULL**. (Zobacz [getenv —](../c-runtime-library/reference/getenv-wgetenv.md) w *odwołanie do biblioteki wykonawczej* dla alternatywna metoda pobierania informacji o zmiennych środowiska.)  
  
 **Microsoft Specific**  
  
 `envp` Parametr jest wskaźnikiem do tablicy ciągów zerem, które reprezentują wartości zmiennych środowiskowych użytkownika. `envp` Parametru mogą być deklarowane jako tablicy wskaźników do `char` (`char *envp[]`) lub jako wskaźnik do wskaźników do `char` (`char **envp`). W **wmain** funkcji `envp` parametru mogą być deklarowane jako tablicy wskaźników do `wchar_t` (`wchar_t *envp[]`) lub jako wskaźnik do wskaźników do `wchar_t` (`wchar_t **envp`). Wskazuje koniec tablicy **NULL** \*wskaźnika. Należy pamiętać, że blok środowiska przekazany do **głównego** lub **wmain** jest "zablokowane" kopię bieżącego środowiska. Jeśli użytkownik zmieni środowiska przez wywołanie _**putenv —** lub `_wputenv`, czy bieżące środowisko (zwrócony przez `getenv` / `_wgetenv` i `_environ` lub `_wenviron` zmienne) ulegnie zmianie, ale blok wskazywana przez `envp` nie zmieni się. `envp` Parametr jest ANSI zgodne C, ale nie w języku C++.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcja main i wykonywanie programu](../c-language/main-function-and-program-execution.md)