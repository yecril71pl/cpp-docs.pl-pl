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
- troubleshooting release builds
- memory [C++], overwrites
ms.assetid: 73cbc1f9-3e33-472d-9880-39a8e9977b95
ms.openlocfilehash: 9bd1cafe40417872d42f2e9e1427e5f2eccad7a7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328869"
---
# <a name="common-problems-when-creating-a-release-build"></a>Typowe problemy podczas tworzenia kompilacji wydania

Podczas programowania zwykle kompilujesz i testujesz kompilację debugowania projektu. Jeśli następnie utworzysz aplikację dla kompilacji wydania, możesz uzyskać naruszenie zasad dostępu.

Na poniższej liście przedstawiono podstawowe różnice między debugowaniem a kompilacją wersji (niedebugowaną). Istnieją inne różnice, ale poniżej przedstawiono podstawowe różnice, które spowodują, że aplikacja zakończy się niepowodzeniem w kompilacji wydania, gdy działa w kompilacji debugowania.

- [Układ sterty](#_core_heap_layout)

- [Kompilacja](#_core_compilation)

- [Obsługa wskaźnika](#_core_pointer_support)

- [Optymalizacje](#_core_optimizations)

Aby uzyskać informacje na temat sposobu przechwytywania błędów kompilacji w kompilacjach debugowania, zobacz opcja kompilatora [/GZ (catch Release-Build Errors in Debug Build)](reference/gz-enable-stack-frame-run-time-error-checking.md) .

## <a name="heap-layout"></a><a name="_core_heap_layout"></a>Układ sterty

Układ sterty będzie przyczyną około 90 procent pozornych problemów, gdy aplikacja działa w debugowaniu, ale nie w wersji.

Podczas kompilowania projektu na potrzeby debugowania jest używany program przydzielania pamięci. Oznacza to, że wszystkie alokacje pamięci mają umieszczane w nich bajty Guard. Te bajty Guard wykrywają zastępowanie pamięci. Ze względu na to, że układ sterty różni się między wersjami i debugowaniem, zastępowanie pamięci może nie spowodować wystąpienia żadnych problemów w kompilacji debugowania, ale mogą one mieć skutki krytyczne w kompilacji wydania.

Aby uzyskać więcej informacji, zobacz [Sprawdzanie nadpisywania pamięci](checking-for-memory-overwrites.md) i [Używanie kompilacji debugowania do sprawdzania nadpisywania pamięci](using-the-debug-build-to-check-for-memory-overwrite.md).

## <a name="compilation"></a><a name="_core_compilation"></a>Kompilowa

Wiele makr MFC i wiele zmian implementacji MFC podczas kompilowania do wydania. W szczególności makro ASSERT zwraca wartość Nothing w kompilacji wydania, więc żaden kod znaleziony w POTWIERDZENIAch nie zostanie wykonany. Aby uzyskać więcej informacji, zobacz temat [Badanie instrukcji Assert](using-verify-instead-of-assert.md).

Niektóre funkcje są podkreślane w celu zwiększenia szybkości kompilacji wydania. Optymalizacje są zwykle włączane w kompilacji wydania. Używany jest również inny Alokator pamięci.

## <a name="pointer-support"></a><a name="_core_pointer_support"></a>Obsługa wskaźnika

Brak informacji o debugowaniu usuwa uzupełnienie z aplikacji. W kompilacji wydania nieużywane wskaźniki są bardziej szansę wskazujące niezainicjowaną pamięć zamiast wskazywać na informacje debugowania.

## <a name="optimizations"></a><a name="_core_optimizations"></a>Optymalizacje

W zależności od charakteru niektórych segmentów kodu kompilator optymalizujący może wygenerować nieoczekiwany kod. Jest to najmniej najprawdopodobniej przyczyną problemów z kompilacją wersji, ale zdarza się to na razie. Aby uzyskać rozwiązanie, zobacz [Optymalizacja kodu](optimizing-your-code.md).

## <a name="see-also"></a>Zobacz też

[Kompilacje wydania](release-builds.md)<br/>
[Naprawianie problemów kompilacji wydania](fixing-release-build-problems.md)
