---
title: /VERBOSE (Drukuj komunikaty o postępie)
ms.date: 11/04/2016
f1_keywords:
- /verbose
- VC.Project.VCLinkerTool.ShowProgress
helpviewer_keywords:
- -VERBOSE linker option
- linking [C++], session progress information
- Print Progress Messages linker option
- linker [C++], output dependency information
- /VERBOSE linker option
- dependencies [C++], dependency information in linker output
- VERBOSE linker option
ms.assetid: 9c347d98-4c37-4724-a39e-0983934693ab
ms.openlocfilehash: 7aed1e17034b40ffdad4da4136fc5a64361b3d77
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809148"
---
# <a name="verbose-print-progress-messages"></a>/VERBOSE (Drukuj komunikaty o postępie)

```
/VERBOSE[:{ICF|INCR|LIB|REF|SAFESEH|UNUSEDLIBS}]
```

## <a name="remarks"></a>Uwagi

Program łączący wysyła informacje o postępie łączenia sesji, do **dane wyjściowe** okna. W wierszu polecenia informacje są wysyłane do wyjścia standardowego i mogą zostać przekierowane do pliku.

|Opcja|Opis|
|------------|-----------------|
|/VERBOSE|Wyświetla szczegóły dotyczące proces łączenia.|
|/VERBOSE:ICF|Wyświetlanie informacji na temat aktywności konsolidatora, które powstały na skutek stosowania [/OPT: ICF](opt-optimizations.md).|
|/VERBOSE:INCR|Wyświetla informacje na temat przyrostowego procesu łączenia.|
|/ VERBOSE: LIB|Wyświetla wiadomości postępu, które wskazują wyłącznie biblioteki przeszukiwane.<br /><br /> Wyświetlane informacje obejmują proces wyszukiwania biblioteki i listy każdej nazwy biblioteki i obiektu (z pełną ścieżką), symbolu zamieniana z biblioteki i listy obiektów, które odwołują się symbol.|
|/ VERBOSE: REF|Przedstawia informacje na temat aktywności konsolidatora, które powstały na skutek stosowania [/OPT: REF](opt-optimizations.md).|
|/ VERBOSE: SAFESEH|Wyświetla informacje dotyczące modułów, które nie są zgodne z wyjątkiem bezpiecznej obsługi, kiedy [opcja/SAFESEH](safeseh-image-has-safe-exception-handlers.md) nie zostanie określony.|
|/ VERBOSE: UNUSEDLIBS|Wyświetla informacje o dowolnych plikach bibliotek, które nie są używane podczas tworzenia obrazu.|

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Rozwiń **konsolidatora** folderu.

1. Wybierz **wiersza polecenia** stronę właściwości.

1. Dodaj opcję **dodatkowe opcje** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ShowProgress%2A>.

## <a name="see-also"></a>Zobacz także

[Odwołania konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
