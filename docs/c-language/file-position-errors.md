---
title: Błędy pozycji w pliku
ms.date: 11/04/2016
helpviewer_keywords:
- file pointers [C++], file position errors
ms.assetid: d5e59d8b-08c0-4927-a338-0b2d8234ce24
ms.openlocfilehash: 3d581d86d6f08eee564feb6373a623512085ccca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233660"
---
# <a name="file-position-errors"></a>Błędy pozycji w pliku

**ANSI 4.9.9.1, 4.9.9.4** wartości, do którego makro `errno` została ustawiona przez `fgetpos` lub `ftell` funkcji w przypadku niepowodzenia

Gdy `fgetpos` lub `ftell` zakończy się niepowodzeniem, `errno` ustawiono stała manifestu `EINVAL` Jeśli pozycja jest nieprawidłowa lub `EBADF` Jeśli liczba plików jest nieprawidłowy. Stałe są definiowane w numer błędu. H.

## <a name="see-also"></a>Zobacz także

[Funkcje bibliotek](../c-language/library-functions.md)
