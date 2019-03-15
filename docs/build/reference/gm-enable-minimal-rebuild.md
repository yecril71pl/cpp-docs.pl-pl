---
title: /Gm (Włącz minimalną ponowną kompilację)
ms.date: 11/12/2018
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
ms.openlocfilehash: 4a66dda37b84119a4b8bc23f7fc719d50e8786f9
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808212"
---
# <a name="gm-enable-minimal-rebuild"></a>/Gm (Włącz minimalną ponowną kompilację)

Przestarzałe. Umożliwia minimalną ponowną kompilację, która określa, czy pliki źródłowe C++, które zawierają zmienione definicje klas C++ (przechowywane w plikach nagłówków (.h)) muszą być ponownie kompilowane.

## <a name="syntax"></a>Składnia

```
/Gm
```

## <a name="remarks"></a>Uwagi

**/GM** jest przestarzała. Nie może to powodować kompilacji dla niektórych rodzajów zmian w plikach nagłówka. Ta opcja może być bezpiecznie usunąć w projektach. Aby skrócić czas kompilacji, firma Microsoft zaleca używał wstępnie skompilowanych nagłówków, a przyrostowe i równoległych opcje kompilacji zamiast tego. Aby uzyskać listę opcji kompilatora przestarzałe zobacz **usunięte opcje kompilatora i uznane za przestarzałe** sekcji [opcje kompilatora wymienione według kategorii](compiler-options-listed-by-category.md).

Kompilator przechowuje informacje o zależnościach między plikami źródłowymi a definicje klas w pliku .idb projektu podczas pierwszej kompilacji. (Informacje o zależnościach informuje, plik źródłowy, który jest zależny od definicji klasy, które, a które. h: plik definicji znajduje się w). Kolejne kompiluje umożliwia informacje przechowywane w pliku .idb ustalić, czy plik źródłowy musi skompilowany, nawet jeśli plik .h zmodyfikowane.

> [!NOTE]
> Minimalna ponowna kompilacja zależy od klasy definicje nie zostanie zmieniona, między dołączania plików. Definicje klas muszą być globalne dla projektu (powinien istnieć tylko jedna definicja danej klasy), ponieważ informacje o zależności w pliku .idb jest tworzone dla całego projektu. Jeśli masz więcej niż jedną definicję klasy w projekcie, należy wyłączyć minimalną ponowną kompilację.

Ponieważ konsolidatora przyrostowego nie obsługuje metadanych Windows dołączona do plików .obj przy użyciu [/ZW (kompilacja środowiska uruchomieniowego Windows)](zw-windows-runtime-compilation.md) opcji **/Gm** opcja jest niezgodna z  **/Zw**.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **generowania kodu** stronę właściwości.

1. Modyfikowanie **Włącz minimalną ponowną kompilację** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.MinimalRebuild%2A>.

## <a name="see-also"></a>Zobacz także

[MSVC Compiler Options](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
