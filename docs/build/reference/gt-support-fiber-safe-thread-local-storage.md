---
title: /GT (Obsługa bezpieczeństwa włókien magazynu wątków lokalnych)
description: Opcja kompilatora MSVC/GT Włącza bezpieczne optymalizacje dla danych magazynu lokalnego wątku.
ms.date: 07/08/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFiberSafeOptimizations
- /gt
helpviewer_keywords:
- /GT compiler option [C++]
- GT compiler option [C++]
- thread-local storage
- static thread-local storage and fiber safety
- -GT compiler option [C++]
- fiber-safe static thread-local storage compiler option [C++]
ms.assetid: 071fec79-c701-432b-9970-457344133159
ms.openlocfilehash: 1b1d9f6514cec8c3d247f86be063f2ac3e0dfe72
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180815"
---
# <a name="gt-support-fiber-safe-thread-local-storage"></a>`/GT`(Obsługa bezpiecznego włókna — magazyn lokalny)

Obsługuje zabezpieczenia włókna danych przydzielonych przy użyciu statycznego magazynu wątków lokalnych, czyli danych przydzielono z `__declspec(thread)` .

## <a name="syntax"></a>Składnia

> **`/GT`**

## <a name="remarks"></a>Uwagi

Dane zadeklarowane za pomocą `__declspec(thread)` są przywoływane przez tablicę magazynu wątków (TLS). Tablica TLS to tablica adresów, którą system obsługuje dla każdego wątku. Każdy adres w tej tablicy umożliwia lokalizację danych magazynu lokalnego wątku.

Włókna światłowodowe są obiektem lekkim, który składa się z stosu i kontekstu rejestru i można zaplanować w różnych wątkach. Włókna można uruchomić na dowolnym wątku. Ze względu na to, że włókna mogą zostać zamienione i ponownie uruchomione później w innym wątku, kompilator nie może w pamięci podręcznej adres tablicy TLS lub optymalizuje jako wspólne Podwyrażenie w wywołaniu funkcji. **`/GT`** uniemożliwia takie optymalizacje.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę właściwości optymalizacji**C/C++** właściwości konfiguracji  >  **Optimization** .

1. Zmodyfikuj właściwość **Włącz optymalizacje bezpieczne dla włókna** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFiberSafeOptimizations%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
