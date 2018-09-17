---
title: -INCLUDE (Wymuszaj odwołania do symboli) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /include
- VC.Project.VCLinkerTool.ForceSymbolReferences
dev_langs:
- C++
helpviewer_keywords:
- INCLUDE linker option
- force symbol references linker option
- symbol references linker force
- /INCLUDE linker option
- symbols, add to symbol table
- -INCLUDE linker option
ms.assetid: 4a039677-360a-480f-bd0b-448e239b449c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6528f6edc51a2dd01e8f91107827b570a44785de
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715783"
---
# <a name="include-force-symbol-references"></a>/INCLUDE (Wymuszaj odwołania do symboli)

```
/INCLUDE:symbol
```

## <a name="parameters"></a>Parametry

*Symbol*<br/>
Określa symbol do dodania do tabeli symboli.

## <a name="remarks"></a>Uwagi

Opcja/include informuje konsolidator, aby dodał określony symbol do tabeli symboli.

Aby określić wiele symboli, wpisz przecinek (,), średnika (;) lub odstęp między nazwy symboli. W wierszu polecenia, należy określić/include:`symbol` jeden raz dla każdego symbolu.

Konsolidator usuwa `symbol` , dodając obiekt, który zawiera definicję symbolu do programu. Ta funkcja jest przydatna, w tym obiektu biblioteki, które w przeciwnym razie nie będzie można połączone z tym programem.

Określanie symbolu z tą opcją zastąpienia usunięcie tego symbolu przez [/OPT: REF](../../build/reference/opt-optimizations.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **dane wejściowe** stronę właściwości.

1. Modyfikowanie **Wymuszaj odwołania do symboli** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ForceSymbolReferences%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)