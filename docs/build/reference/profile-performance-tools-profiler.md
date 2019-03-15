---
title: /PROFILE (Profiler narzędzi do oceny wydajności)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.Profile
helpviewer_keywords:
- -PROFILE linker option
- /PROFILE linker option
ms.assetid: e676baa1-5063-47a3-a357-ba0d1f0d1699
ms.openlocfilehash: ca68ae090c6e4e6e3e10f37ac0d225faee96746a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810006"
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

## <a name="see-also"></a>Zobacz także

[Odwołania konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
