---
title: Kompilacje wydania
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [C++], release builds
- release builds
- debug builds, converting to release build
ms.assetid: fa9a78fa-f4b5-4722-baf4-aec655c4ff0f
ms.openlocfilehash: 77e02b424b10b5e9606cc49152c2e21d7eeed9cb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667457"
---
# <a name="release-builds"></a>Kompilacje wydania

Kompilację wydania używa optymalizacji. Gdy używasz optymalizacji utworzyć kompilację wydania, kompilator nie generuje symboliczne informacje debugowania. Brak symboliczne informacje debugowania, a także fakt, czy kod nie jest generowany dla śledzenia i ASERCJA wywołuje, oznacza to, że rozmiar pliku wykonywalnego jest krótszy, a więc będą szybciej.

W tej sekcji przedstawiono informacje, na kiedy i dlaczego chcesz zmienić z kompilacji debugowania do kompilacji wydania. Omówiono w nim również niektóre problemy, które można napotkać podczas zmiany z poziomu pozycji Debuguj kompilację wydania:

- [Tworzenie kompilacji wydania](../../build/reference/how-to-create-a-release-build.md)

- [Typowe problemy podczas tworzenia kompilacji wydania](../../build/reference/common-problems-when-creating-a-release-build.md)

- [Naprawianie problemów kompilacji wydania](../../build/reference/fixing-release-build-problems.md)

   - [Badanie Assert-instrukcje](../../build/reference/using-verify-instead-of-assert.md)

   - [Korzystanie z kompilacji debugowania do sprawdzania nadpisywania pamięci](../../build/reference/using-the-debug-build-to-check-for-memory-overwrite.md)

   - [Debugowanie kompilacji wydania](../../build/reference/how-to-debug-a-release-build.md)

   - [Sprawdzanie nadpisywania pamięci](../../build/reference/checking-for-memory-overwrites.md)

## <a name="see-also"></a>Zobacz też

[Kompilowanie projektów C++ w Visual Studio](../../ide/building-cpp-projects-in-visual-studio.md)<br/>
[Dokumentacja kompilacji w języku C/C++](../../build/reference/c-cpp-building-reference.md)