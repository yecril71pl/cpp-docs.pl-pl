---
title: /INCLUDE (Wymuszaj odwołania do symboli)
ms.date: 11/04/2016
f1_keywords:
- /include
- VC.Project.VCLinkerTool.ForceSymbolReferences
helpviewer_keywords:
- INCLUDE linker option
- force symbol references linker option
- symbol references linker force
- /INCLUDE linker option
- symbols, add to symbol table
- -INCLUDE linker option
ms.assetid: 4a039677-360a-480f-bd0b-448e239b449c
ms.openlocfilehash: 1f7a443e32ed20550e3017c7e6ce70f4adf5137d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810981"
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

Określanie symbolu z tą opcją zastąpienia usunięcie tego symbolu przez [/OPT: REF](opt-optimizations.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **dane wejściowe** stronę właściwości.

1. Modyfikowanie **Wymuszaj odwołania do symboli** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ForceSymbolReferences%2A>.

## <a name="see-also"></a>Zobacz także

[Odwołania konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
