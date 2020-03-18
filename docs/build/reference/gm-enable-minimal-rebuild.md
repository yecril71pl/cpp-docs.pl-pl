---
title: /Gm (Włącz minimalną ponowną kompilację)
ms.date: 11/12/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.MinimalRebuild
- /Gm
- VC.Project.VCCLWCECompilerTool.MinimalRebuild
helpviewer_keywords:
- /Gm compiler option [C++]
- minimal rebuild
- enable minimal rebuild compiler option [C++]
- Gm compiler option [C++]
- -Gm compiler option [C++]
ms.assetid: d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59
ms.openlocfilehash: 9b928f3add0a2ec10257bf63fe61a824336c19b8
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439639"
---
# <a name="gm-enable-minimal-rebuild"></a>/Gm (Włącz minimalną ponowną kompilację)

Przestarzałe. Włącza minimalną ponowną kompilację C++ , która określa, czy C++ pliki źródłowe, które zawierają zmienione definicje klas (przechowywane w plikach nagłówkowych (h)), muszą być ponownie skompilowane.

## <a name="syntax"></a>Składnia

```
/Gm
```

## <a name="remarks"></a>Uwagi

**/GM** jest przestarzała. Nie może wyzwolić kompilacji dla niektórych rodzajów zmian plików nagłówkowych. Możesz bezpiecznie usunąć tę opcję z projektów. W celu skrócenia czasu kompilacji zalecamy używanie prekompilowanych nagłówków i opcji kompilacji przyrostowej i równoległej. Aby zapoznać się z listą przestarzałych opcji kompilatora, zobacz sekcję **przestarzałe i usunięte opcje kompilatora** w [opcjach kompilatora wymienionych według kategorii](compiler-options-listed-by-category.md).

Kompilator przechowuje informacje o zależnościach między plikami źródłowymi i definicjami klas w pliku. idb projektu podczas pierwszej kompilacji. (Informacje o zależnościach wskazują, który plik źródłowy jest zależny od definicji klasy i pliku h, w którym znajduje się definicja). Kolejne kompilacje wykorzystują informacje przechowywane w pliku. IDB, aby określić, czy plik źródłowy musi zostać skompilowany, nawet jeśli zawiera zmodyfikowany plik h.

> [!NOTE]
> Minimalna ponowna kompilacja opiera się na definicjach klas, które nie zmieniają się między dołączanymi plikami. Definicje klas muszą być globalne dla projektu (powinna istnieć tylko jedna definicja danej klasy), ponieważ informacje o zależnościach w pliku IDB są tworzone dla całego projektu. Jeśli masz więcej niż jedną definicję klasy w projekcie, wyłącz minimalną ponowną kompilację.

Ponieważ przyrostowy konsolidator nie obsługuje metadanych systemu Windows uwzględnionych w plikach. obj przy użyciu opcji [/zw (kompilacja środowisko wykonawcze systemu Windows)](zw-windows-runtime-compilation.md) , opcja **/GM** jest niezgodna z **/zw**.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Właściwości konfiguracji** > stronie właściwości **generowanie kodu** **C++ C/**  > .

1. Zmodyfikuj właściwość **Włącz minimalną** ponowną kompilację.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.MinimalRebuild%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
