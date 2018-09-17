---
title: -PROFILE (Profiler narzędzi wydajności) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.Profile
dev_langs:
- C++
helpviewer_keywords:
- -PROFILE linker option
- /PROFILE linker option
ms.assetid: e676baa1-5063-47a3-a357-ba0d1f0d1699
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 859ea4091502fa6c339a809a5b9e439c91462bd7
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707770"
---
# <a name="profile-performance-tools-profiler"></a>/PROFILE (Profiler narzędzi do oceny wydajności)

Tworzy plik wyjściowy, który może służyć z profilerem narzędzi wydajności.

## <a name="syntax"></a>Składnia

```
/PROFILE
```

## <a name="remarks"></a>Uwagi

PROFIL wymaga następujących opcji konsolidatora:

- [/ OPT: REF](../../build/reference/opt-optimizations.md)

- / OPT: NOICF

- [/ INCREMENTAL: NO](../../build/reference/incremental-link-incrementally.md)

- [/ FIXED: NO](../../build/reference/fixed-fixed-base-address.md)

PROFIL, powoduje, że konsolidator generuje sekcji relokacji w obrazie programu.  Relokacji umożliwia profiler do przekształcania obrazu programu, który można pobrać danych profilu.

**/ PROFILE** tylko jest dostępna tylko w wersjach Enterprise (Projektowanie zespołowe).  Aby uzyskać więcej informacji na temat PREfast, zobacz [analiza kodu C/C++ — Przegląd](/visualstudio/code-quality/code-analysis-for-c-cpp-overview).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Rozwiń **właściwości konfiguracji** węzła.

1. Rozwiń **konsolidatora** węzła.

1. Wybierz **zaawansowane** stronę właściwości.

1. Modyfikowanie **profilu** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Profile%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)