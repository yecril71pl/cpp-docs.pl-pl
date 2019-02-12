---
title: Błędy pozycji w pliku
ms.date: 11/04/2016
helpviewer_keywords:
- file pointers [C++], file position errors
ms.assetid: d5e59d8b-08c0-4927-a338-0b2d8234ce24
ms.openlocfilehash: 3d581d86d6f08eee564feb6373a623512085ccca
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147805"
---
# <a name="file-position-errors"></a>Błędy pozycji w pliku

**ANSI 4.9.9.1, 4.9.9.4** wartości, do którego makro `errno` została ustawiona przez `fgetpos` lub `ftell` funkcji w przypadku niepowodzenia

Gdy `fgetpos` lub `ftell` zakończy się niepowodzeniem, `errno` ustawiono stała manifestu `EINVAL` Jeśli pozycja jest nieprawidłowa lub `EBADF` Jeśli liczba plików jest nieprawidłowy. Stałe są definiowane w numer błędu. H.

## <a name="see-also"></a>Zobacz także

[Funkcje bibliotek](../c-language/library-functions.md)
