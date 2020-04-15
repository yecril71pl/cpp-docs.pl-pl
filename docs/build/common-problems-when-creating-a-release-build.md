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

Podczas tworzenia zwykle będzie tworzyć i testować za pomocą kompilacji debugowania projektu. Jeśli następnie skompilować aplikację dla kompilacji wydania, może uzyskać naruszenie zasad dostępu.

Poniższa lista przedstawia podstawowe różnice między debugowania i wersji (nondebug) kompilacji. Istnieją inne różnice, ale poniżej są podstawowe różnice, które mogłyby spowodować, że aplikacja zakończy się niepowodzeniem w kompilacji wydania, gdy działa w kompilacji debugowania.

- [Układ sterty](#_core_heap_layout)

- [Kompilacja](#_core_compilation)

- [Obsługa wskaźnika](#_core_pointer_support)

- [Optymalizacje](#_core_optimizations)

Zobacz [/GZ (Catch Release-Build błędy w debugowania kompilacji)](reference/gz-enable-stack-frame-run-time-error-checking.md) opcja kompilatora informacji na temat sposobu połowu błędów kompilacji wydania w kompilacji debugowania.

## <a name="heap-layout"></a><a name="_core_heap_layout"></a>Układ sterty

Układ sterty będzie przyczyną około dziewięćdziesięciu procent problemów, gdy aplikacja działa w debugowaniu, ale nie zwalnia.

Podczas tworzenia projektu do debugowania, używasz alokatora pamięci debugowania. Oznacza to, że wszystkie alokacje pamięci mają bajty straży umieszczone wokół nich. Te bajty straży wykryć zastąpienie pamięci. Ponieważ układ sterty różni się między wersjami wersji i debugowania, zastąpienie pamięci może nie powodować żadnych problemów w kompilacji debugowania, ale może mieć katastrofalne skutki w kompilacji wydania.

Aby uzyskać więcej informacji, zobacz [Sprawdzanie zastępowania pamięci](checking-for-memory-overwrites.md) i używanie [kompilacji debugowania do sprawdzania zastępowania pamięci](using-the-debug-build-to-check-for-memory-overwrite.md).

## <a name="compilation"></a><a name="_core_compilation"></a>Kompilacji

Wiele makr MFC i wiele zmian implementacji MFC podczas tworzenia do wydania. W szczególności makra ASSERT ocenia nic w kompilacji wydania, więc żaden z kodu znalezionego w ASSERTs zostaną wykonane. Aby uzyskać więcej informacji, zobacz [Badanie instrukcji ASSERT](using-verify-instead-of-assert.md).

Niektóre funkcje są inlined dla zwiększonej szybkości w kompilacji wydania. Optymalizacje są zazwyczaj włączone w kompilacji wydania. Używany jest również inny alokator pamięci.

## <a name="pointer-support"></a><a name="_core_pointer_support"></a>Obsługa wskaźnika

Brak informacji debugowania usuwa dopełnienie z aplikacji. W kompilacji wydania bezpańskich wskaźników mają większe szanse na wskazanie niezainicjowanej pamięci zamiast wskazując na informacje debugowania.

## <a name="optimizations"></a><a name="_core_optimizations"></a>Optymalizacje

W zależności od charakteru niektórych segmentów kodu kompilator optymalizacji może generować nieoczekiwany kod. Jest to najmniej prawdopodobna przyczyna problemów kompilacji wydania, ale pojawia się czasami. Aby uzyskać rozwiązanie, zobacz [Optymalizacja kodu](optimizing-your-code.md).

## <a name="see-also"></a>Zobacz też

[Kompilacje wydania](release-builds.md)<br/>
[Naprawianie problemów kompilacji wydania](fixing-release-build-problems.md)
