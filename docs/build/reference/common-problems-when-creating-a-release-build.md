---
title: Typowe problemy podczas tworzenia kompilacji wydania
ms.date: 11/04/2016
helpviewer_keywords:
- unexpected code generation
- debugging [MFC], release builds
- release builds, troubleshooting
- stray pointers
- debug builds, difference from release builds
- MFC [C++], release builds
- heap layout problems
- pointers, stray
- release builds, building applications
- debug memory allocator
- optimization [C++], compiler
- projects [C++], debug configuration
- troubleshooting Visual C++
- troubleshooting release builds
- memory [C++], overwrites
ms.assetid: 73cbc1f9-3e33-472d-9880-39a8e9977b95
ms.openlocfilehash: a19eabc7b3e334f4a2a6d967d2bfc81b080c0054
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546568"
---
# <a name="common-problems-when-creating-a-release-build"></a>Typowe problemy podczas tworzenia kompilacji wydania

Podczas tworzenia aplikacji będzie zazwyczaj kompilowania i testowania z kompilacji debugowania projektu. Jeśli następnie utworzysz aplikację dla kompilacji oficjalnej, może zostać naruszenie zasad dostępu.

Poniższa lista zawiera podstawowe różnice między debugowania, jak i kompilację wydania (nondebug). Istnieją inne różnice, ale poniżej przedstawiono podstawowe różnice, które mogłoby spowodować awarię aplikacji kompilację wydania, gdy działa w kompilacji debugowania.

- [Układ stosu](#_core_heap_layout)

- [Kompilacja](#_core_compilation)

- [Obsługa wskaźnika](#_core_pointer_support)

- [Optymalizacje](#_core_optimizations)

Zobacz [GZ (przechwytywać błędy kompilacji wydania w kompilacji debugowania)](../../build/reference/gz-enable-stack-frame-run-time-error-checking.md) — opcja kompilatora informacji na temat sposobu catch wersji kompilacji błędy w kompilacjach do debugowania.

##  <a name="_core_heap_layout"></a> Układ stosu

Układ stosu jest przyczyną około 90% widocznych problemów, jeśli aplikacja działa w debugowania, ale nie wersji.

Podczas kompilowania projektu do debugowania używają alokatora pamięci debugowania. Oznacza to, czy wszystkie alokacje pamięci mają bajtów guard umieszczone wokół nich. Te bajtów guard wykryć Zastąp pamięci. Ponieważ układ sterty różni się między Zwolnij i Debuguj wersje, Zastąp pamięci nie może utworzyć wszelkie problemy w kompilacji debugowania, ale mogą mieć wpływ krytycznego kompilację wydania.

Aby uzyskać więcej informacji, zobacz [sprawdzaj zastąpić pamięci](../../build/reference/checking-for-memory-overwrites.md) i [na użytek debugowanie kompilacji Aby sprawdzić zastąpić pamięci](../../build/reference/using-the-debug-build-to-check-for-memory-overwrite.md).

##  <a name="_core_compilation"></a> Kompilacja

Wiele z makr MFC i większość zmian implementacji MFC, podczas tworzenia wersji. W szczególności ASSERT — makro daje w wyniku nic w kompilacji wydania, więc żaden kod w potwierdzenia zostaną wykonane. Aby uzyskać więcej informacji, zobacz [zbadać instrukcjami ASSERT](../../build/reference/using-verify-instead-of-assert.md).

Niektóre funkcje są śródwierszowych dla zwiększona szybkość w kompilacji wydania. Optymalizacje ogólnie są włączone w kompilacji wydania. Alokator pamięci różnych jest również używany.

##  <a name="_core_pointer_support"></a> Obsługa wskaźnika

Brak informacji o debugowaniu usuwa uzupełnienie z aplikacji. W kompilacji wydania wskaźniki stray mają większe prawdopodobieństwo wskazujący niezainicjowanej pamięci, a nie wskazuje na informacje o debugowaniu.

##  <a name="_core_optimizations"></a> Optymalizacje

W zależności od charakteru niektórych fragmentów kodu kompilatora optymalizującego może generować nieoczekiwany kod. To jest najmniej prawdopodobne przyczyny problemów kompilacji wydania, ale czasami wystąpić. Dla rozwiązania, zobacz [optymalizacji kodu](../../build/reference/optimizing-your-code.md).

## <a name="see-also"></a>Zobacz też

[Kompilacje wydania](../../build/reference/release-builds.md)<br/>
[Naprawianie problemów kompilacji wydania](../../build/reference/fixing-release-build-problems.md)