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

**4.9.9.1 ANSI, 4.9.9.4** Wartość, dla której makro `errno` jest ustawiane przez funkcję `fgetpos` lub `ftell` w przypadku niepowodzenia

Gdy `fgetpos` lub `ftell` niepowodzenie `errno` , jest ustawiona na stałą `EINVAL` manifestu, jeśli pozycja jest nieprawidłowa lub `EBADF` Jeśli numer pliku jest nieodpowiedni. Stałe są zdefiniowane w ERRNO. C.

## <a name="see-also"></a>Zobacz też

[Funkcje bibliotek](../c-language/library-functions.md)
