---
title: Kompilacje wydania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging [C++], release builds
- release builds
- debug builds, converting to release build
ms.assetid: fa9a78fa-f4b5-4722-baf4-aec655c4ff0f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f3ae18c5e2dcdb735880509fd158dac4ccaa1462
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="release-builds"></a>Kompilacje wydania
Kompilacji wydania używa optymalizacji. Podczas optymalizacji umożliwia tworzenie kompilacji wydania, kompilator nie przyniesie symboliczna informacja o debugowaniu. Brak symboliczne informacje debugowania, a także fakt nie wygenerować kodu dla śledzenia i ASSERT wywołuje oznacza, że rozmiar pliku wykonywalnego, zostanie zmniejszona i w związku z tym będzie można szybciej.  
  
 W tej sekcji przedstawiono informacje na kiedy i dlaczego należy zmienić z kompilacji debugowania do kompilacji wydania. Omówiono w nim również niektóre problemy, które można napotkać podczas zmiany z debugowanie kompilacji wydania:  
  
-   [Tworzenie kompilacji wydania](../../build/reference/how-to-create-a-release-build.md)  
  
-   [Typowe problemy podczas tworzenia kompilacji wydania](../../build/reference/common-problems-when-creating-a-release-build.md)  
  
-   [Naprawianie problemów kompilacji wydania](../../build/reference/fixing-release-build-problems.md)  
  
    -   [Badanie ASSERT-instrukcje](../../build/reference/using-verify-instead-of-assert.md)  
  
    -   [Korzystanie z kompilacji debugowania do sprawdzania nadpisywania pamięci](../../build/reference/using-the-debug-build-to-check-for-memory-overwrite.md)  
  
    -   [Debugowanie kompilacji wydania](../../build/reference/how-to-debug-a-release-build.md)  
  
    -   [Sprawdzanie nadpisywania pamięci](../../build/reference/checking-for-memory-overwrites.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilowanie projektów C++ w programie Visual Studio](../../ide/building-cpp-projects-in-visual-studio.md)   
 [Dokumentacja kompilacji w języku C/C++](../../build/reference/c-cpp-building-reference.md)