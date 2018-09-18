---
title: Błędy pozycji w pliku | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- file pointers [C++], file position errors
ms.assetid: d5e59d8b-08c0-4927-a338-0b2d8234ce24
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8def11317548bfd6e70badab4563891c1b6f864d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031924"
---
# <a name="file-position-errors"></a>Błędy pozycji w pliku

**ANSI 4.9.9.1, 4.9.9.4** wartości, do którego makro `errno` została ustawiona przez `fgetpos` lub `ftell` funkcji w przypadku niepowodzenia

Gdy `fgetpos` lub `ftell` zakończy się niepowodzeniem, `errno` ustawiono stała manifestu `EINVAL` Jeśli pozycja jest nieprawidłowa lub `EBADF` Jeśli liczba plików jest nieprawidłowy. Stałe są definiowane w numer błędu. H.

## <a name="see-also"></a>Zobacz też

[Funkcje bibliotek](../c-language/library-functions.md)
