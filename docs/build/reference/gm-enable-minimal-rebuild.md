---
title: /Gm (Włącz minimalną ponowną kompilację)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.MinimalRebuild
- /Gm
- /FD
- VC.Project.VCCLWCECompilerTool.MinimalRebuild
helpviewer_keywords:
- /Gm compiler option [C++]
- minimal rebuild
- enable minimal rebuild compiler option [C++]
- Gm compiler option [C++]
- -Gm compiler option [C++]
ms.assetid: d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59
ms.openlocfilehash: 2a5bc4008ab9376367b3a32040c2a4a70147187f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50570407"
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