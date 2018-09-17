---
title: -Gm-(Włącz minimalną ponowną kompilację) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.MinimalRebuild
- /Gm
- /FD
- VC.Project.VCCLWCECompilerTool.MinimalRebuild
dev_langs:
- C++
helpviewer_keywords:
- /Gm compiler option [C++]
- minimal rebuild
- enable minimal rebuild compiler option [C++]
- Gm compiler option [C++]
- -Gm compiler option [C++]
ms.assetid: d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0f18881e79a3f82941f04dccbde210b2c62dcbca
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725767"
---
# <a name="gm-enable-minimal-rebuild"></a>/Gm (Włącz minimalną ponowną kompilację)

Umożliwia minimalną ponowną kompilację, która określa, czy pliki źródłowe C++, które zawierają zmienione definicje klas C++ (przechowywane w plikach nagłówków (.h)) muszą być ponownie kompilowane.

## <a name="syntax"></a>Składnia

```
/Gm
```

## <a name="remarks"></a>Uwagi

Kompilator przechowuje informacje o zależnościach między plikami źródłowymi a definicje klas w pliku .idb projektu podczas pierwszej kompilacji. (Informacje o zależnościach informuje, plik źródłowy, który jest zależny od definicji klasy, które, a które. h: plik definicji znajduje się w). Kolejne kompiluje umożliwia informacje przechowywane w pliku .idb ustalić, czy plik źródłowy musi skompilowany, nawet jeśli plik .h zmodyfikowane.

> [!NOTE]
>  Minimalna ponowna kompilacja zależy od klasy definicje nie zostanie zmieniona, między dołączania plików. Definicje klas muszą być globalne dla projektu (powinien istnieć tylko jedna definicja danej klasy), ponieważ informacje o zależności w pliku .idb jest tworzone dla całego projektu. Jeśli masz więcej niż jedną definicję klasy w projekcie, należy wyłączyć minimalną ponowną kompilację.

Ponieważ konsolidatora przyrostowego nie obsługuje metadanych Windows dołączona do plików .obj przy użyciu [/ZW (kompilacja środowiska uruchomieniowego Windows)](../../build/reference/zw-windows-runtime-compilation.md) opcji **/Gm** opcja jest niezgodna z  **/Zw**.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **generowania kodu** stronę właściwości.

1. Modyfikowanie **Włącz minimalną ponowną kompilację** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.MinimalRebuild%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)