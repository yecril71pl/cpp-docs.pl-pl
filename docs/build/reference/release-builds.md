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
ms.openlocfilehash: 4b8d4f0d9b1bf0401cc6630b61449e87d72ff675
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722127"
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