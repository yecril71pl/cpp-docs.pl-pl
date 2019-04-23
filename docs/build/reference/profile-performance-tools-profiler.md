---
title: /PROFILE (Profiler narzędzi do oceny wydajności)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.Profile
helpviewer_keywords:
- -PROFILE linker option
- /PROFILE linker option
ms.assetid: e676baa1-5063-47a3-a357-ba0d1f0d1699
ms.openlocfilehash: 23cbccba9a8ec839252d553cc5cbafd37e66bbf9
ms.sourcegitcommit: 14b292596bc9b9b883a9c58cd3e366b282a1f7b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60124775"
---
# <a name="profile-performance-tools-profiler"></a>/PROFILE (Profiler narzędzi do oceny wydajności)

Tworzy plik wyjściowy, który może służyć z profilerem narzędzi wydajności.

## <a name="syntax"></a>Składnia

```
/PROFILE
```

## <a name="remarks"></a>Uwagi

PROFIL wymaga następujących opcji konsolidatora:

- [/ OPT: REF](opt-optimizations.md)

- /OPT:NOICF

- [/ INCREMENTAL: NO](incremental-link-incrementally.md)

- [/ FIXED: NO](fixed-fixed-base-address.md)

PROFIL, powoduje, że konsolidator generuje sekcji relokacji w obrazie programu.  Relokacji umożliwia profiler do przekształcania obrazu programu, który można pobrać danych profilu.

**/ PROFILE** tylko jest dostępna tylko w wersjach Enterprise (Projektowanie zespołowe).  Aby uzyskać więcej informacji na temat PREfast, zobacz [analiza kodu C/C++ — Przegląd](/visualstudio/code-quality/code-analysis-for-c-cpp-overview).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Rozwiń **właściwości konfiguracji** węzła.

1. Rozwiń **konsolidatora** węzła.

1. Wybierz **zaawansowane** stronę właściwości.

1. Modyfikowanie **profilu** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Profile%2A>.

### <a name="to-set-this-linker-option-within-visual-studio-cmake-project"></a>Aby ustawić tę opcję konsolidatora w ramach projektu programu Visual Studio narzędzia CMake

**Narzędzie CMake** projekt nie ma **stron właściwości**, opcje konsolidatora można ustawić, modifing pliku CMakeLists.txt.

1. Otwieranie pliku CMakeLists.txt w katalogu głównym projektu.

1. Dodaj poniższy kod. Aby uzyskać więcej informacji, zobacz [odwołania do narzędzia CMake](https://cmake.org/cmake/help/v3.0/command/set_target_properties.html)

1. Ponownie skompiluj rozwiązanie.

```
SET_TARGET_PROPERTIES(${PROJECT_NAME} PROPERTIES LINK_FLAGS "/PROFILE")
```

## <a name="see-also"></a>Zobacz też

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)

