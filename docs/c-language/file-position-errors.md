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
ms.openlocfilehash: 71c059939891680b638e8644f7902d54452f5332
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383224"
---
# <a name="file-position-errors"></a>Błędy pozycji w pliku
**ANSI 4.9.9.1, 4.9.9.4** wartość, do której makra `errno` jest ustawiana przez `fgetpos` lub `ftell` funkcji w przypadku awarii  
  
 Gdy `fgetpos` lub `ftell` zakończy się niepowodzeniem, `errno` ma ustawioną wartość stała manifestu `EINVAL` Jeśli pozycja jest nieprawidłowy lub `EBADF` Jeśli liczba plików jest nieprawidłowy. Stałe są definiowane w numer błędu. H.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje bibliotek](../c-language/library-functions.md)
