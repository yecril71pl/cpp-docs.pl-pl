---
title: /PROFILE (Profiler narzędzi do oceny wydajności)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.Profile
helpviewer_keywords:
- -PROFILE linker option
- /PROFILE linker option
ms.assetid: e676baa1-5063-47a3-a357-ba0d1f0d1699
ms.openlocfilehash: 07952c979fd66291b1744521d83e4556f010d297
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500781"
---
# <a name="profile-performance-tools-profiler"></a>/PROFILE (Profiler narzędzi do oceny wydajności)

Tworzy plik wyjściowy, który może być używany z profilerem narzędzi wydajności.

## <a name="syntax"></a>Składnia

```
/PROFILE
```

## <a name="remarks"></a>Uwagi

/PROFILE implikuje następujące opcje konsolidatora:

- [/OPT: REF](opt-optimizations.md)

- /OPT: NOICF

- [/INCREMENTAL: NIE](incremental-link-incrementally.md)

- [/FIXED: NIE](fixed-fixed-base-address.md)

/PROFILE powoduje, że konsolidator generuje sekcję relokacji w obrazie programu.  Sekcja relokacja umożliwia programowi Profiler przekształcenie obrazu programu w celu pobrania danych profilu.

**/Profile** jest dostępny tylko w wersjach Enterprise (Development Team).  Aby uzyskać więcej informacji o szybkim przeniesieniu, zobacz [Analiza kodu dla C/C++ — Omówienie](../../code-quality/code-analysis-for-c-cpp-overview.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Rozwiń węzeł **Właściwości konfiguracji** .

1. Rozwiń węzeł **konsolidatora** .

1. Wybierz stronę właściwości **Zaawansowane** .

1. Zmodyfikuj właściwość **profilu** .

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Profile%2A>.

### <a name="to-set-this-linker-option-within-visual-studio-cmake-project"></a>Aby ustawić tę opcję konsolidatora w projekcie programu Visual Studio CMake

Projekt **CMAKE** nie ma **stron właściwości**, a Opcje konsolidatora można ustawić przez modifing CMakeLists.txt.

1. Otwórz CMakeLists.txt w katalogu głównym projektu.

1. Dodaj poniższy kod. Aby uzyskać szczegółowe informacje, zobacz [CMAKE References](https://cmake.org/cmake/help/v3.0/command/set_target_properties.html)

1. Ponownie skompiluj rozwiązanie.

```
SET_TARGET_PROPERTIES(${PROJECT_NAME} PROPERTIES LINK_FLAGS "/PROFILE")
```

## <a name="see-also"></a>Zobacz też

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[MSVC Opcje konsolidatora](linker-options.md)
