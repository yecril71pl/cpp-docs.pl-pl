---
title: Błędy pozycji w pliku
ms.date: 11/04/2016
helpviewer_keywords:
- file pointers [C++], file position errors
ms.assetid: d5e59d8b-08c0-4927-a338-0b2d8234ce24
ms.openlocfilehash: f8c1d5dfc6a599533ce8c1dcfa624d2595779f2b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554612"
---
# <a name="file-position-errors"></a>Błędy pozycji w pliku

**ANSI 4.9.9.1, 4.9.9.4** wartości, do którego makro `errno` została ustawiona przez `fgetpos` lub `ftell` funkcji w przypadku niepowodzenia

Gdy `fgetpos` lub `ftell` zakończy się niepowodzeniem, `errno` ustawiono stała manifestu `EINVAL` Jeśli pozycja jest nieprawidłowa lub `EBADF` Jeśli liczba plików jest nieprawidłowy. Stałe są definiowane w numer błędu. H.

## <a name="see-also"></a>Zobacz też

[Funkcje bibliotek](../c-language/library-functions.md)
