---
title: Kompilacje wersji języka C++ — Visual Studio
ms.date: 12/10/2018
helpviewer_keywords:
- debugging [C++], release builds
- release builds
- debug builds, converting to release build
ms.assetid: fa9a78fa-f4b5-4722-baf4-aec655c4ff0f
ms.openlocfilehash: 46ae5e0f3d545f0e3e004f612314ab416b270fd8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168827"
---
# <a name="release-builds"></a>Kompilacje wydania

Kompilacja wydania używa optymalizacji. W przypadku korzystania z optymalizacji do tworzenia kompilacji wydania kompilator nie będzie generował symbolicznych informacji o debugowaniu. Brak symbolicznych informacji debugowania, wraz z faktem, że kod nie jest generowany dla wywołań śledzenia i POTWIERDZAnia, oznacza, że rozmiar pliku wykonywalnego jest zmniejszany i w związku z tym będzie szybszy.

## <a name="in-this-section"></a>W tej sekcji

[Typowe problemy podczas tworzenia kompilacji wydania](common-problems-when-creating-a-release-build.md)<br/>
[Naprawianie problemów kompilacji wydania](fixing-release-build-problems.md)<br/>
[Korzystanie z VERIFY zamiast ASSERT](using-verify-instead-of-assert.md)<br/>
[Korzystanie z kompilacji debugowania do sprawdzania nadpisywania pamięci](using-the-debug-build-to-check-for-memory-overwrite.md)<br/>
[Instrukcje: debugowanie kompilacji wydania](how-to-debug-a-release-build.md)<br/>
[Sprawdzanie nadpisywania pamięci](checking-for-memory-overwrites.md)<br/>
[Optymalizacja kodu](optimizing-your-code.md)

## <a name="see-also"></a>Zobacz też

[Odwołanie kompilacji C/C++](reference/c-cpp-building-reference.md)
