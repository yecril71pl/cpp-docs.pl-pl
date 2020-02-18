---
title: /PROFILE (Profiler narzędzi do oceny wydajności)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.Profile
helpviewer_keywords:
- -PROFILE linker option
- /PROFILE linker option
ms.assetid: e676baa1-5063-47a3-a357-ba0d1f0d1699
ms.openlocfilehash: 678816ce455d2a982ff8218becd805a0b2cdd896
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416033"
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

**/Profile** jest dostępny tylko w wersjach Enterprise (Development Team).  Aby uzyskać więcej informacji o szybkim przeniesieniu, zobacz [AnalizaC++ kodu dla języka C/przegląd](/cpp/code-quality/code-analysis-for-c-cpp-overview).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Rozwiń węzeł **Właściwości konfiguracji** .

1. Rozwiń węzeł **konsolidatora** .

1. Wybierz stronę właściwości **Zaawansowane** .

1. Zmodyfikuj właściwość **profilu** .

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Profile%2A>.

### <a name="to-set-this-linker-option-within-visual-studio-cmake-project"></a>Aby ustawić tę opcję konsolidatora w projekcie programu Visual Studio CMake

Projekt **CMAKE** nie zawiera **stron właściwości**. Opcje konsolidatora można ustawić przez modifing CMakeLists. txt.

1. Otwórz CMakeLists. txt w katalogu głównym projektu.

1. Dodaj poniższy kod. Aby uzyskać szczegółowe informacje, zobacz [CMAKE References](https://cmake.org/cmake/help/v3.0/command/set_target_properties.html)

1. Ponownie skompiluj rozwiązanie.

```
SET_TARGET_PROPERTIES(${PROJECT_NAME} PROPERTIES LINK_FLAGS "/PROFILE")
```

## <a name="see-also"></a>Zobacz też

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)

