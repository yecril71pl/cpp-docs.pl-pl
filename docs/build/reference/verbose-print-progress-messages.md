---
title: -VERBOSE (Drukuj komunikaty o postępie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /verbose
- VC.Project.VCLinkerTool.ShowProgress
dev_langs:
- C++
helpviewer_keywords:
- -VERBOSE linker option
- linking [C++], session progress information
- Print Progress Messages linker option
- linker [C++], output dependency information
- /VERBOSE linker option
- dependencies [C++], dependency information in linker output
- VERBOSE linker option
ms.assetid: 9c347d98-4c37-4724-a39e-0983934693ab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6acffba952ad46e2b6051aed7effeb4a613bfc65
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725611"
---
# <a name="verbose-print-progress-messages"></a>/VERBOSE (Drukuj komunikaty o postępie)

```
/VERBOSE[:{ICF|INCR|LIB|REF|SAFESEH|UNUSEDLIBS}]
```

## <a name="remarks"></a>Uwagi

Program łączący wysyła informacje o postępie łączenia sesji, do **dane wyjściowe** okna. W wierszu polecenia informacje są wysyłane do wyjścia standardowego i mogą zostać przekierowane do pliku.

|Opcja|Opis|
|------------|-----------------|
|/ VERBOSE|Wyświetla szczegóły dotyczące proces łączenia.|
|/ VERBOSE: ICF|Wyświetlanie informacji na temat aktywności konsolidatora, które powstały na skutek stosowania [/OPT: ICF](../../build/reference/opt-optimizations.md).|
|/ VERBOSE: INCR|Wyświetla informacje na temat przyrostowego procesu łączenia.|
|/ VERBOSE: LIB|Wyświetla wiadomości postępu, które wskazują wyłącznie biblioteki przeszukiwane.<br /><br /> Wyświetlane informacje obejmują proces wyszukiwania biblioteki i listy każdej nazwy biblioteki i obiektu (z pełną ścieżką), symbolu zamieniana z biblioteki i listy obiektów, które odwołują się symbol.|
|/ VERBOSE: REF|Przedstawia informacje na temat aktywności konsolidatora, które powstały na skutek stosowania [/OPT: REF](../../build/reference/opt-optimizations.md).|
|/ VERBOSE: SAFESEH|Wyświetla informacje dotyczące modułów, które nie są zgodne z wyjątkiem bezpiecznej obsługi, kiedy [opcja/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md) nie zostanie określony.|
|/ VERBOSE: UNUSEDLIBS|Wyświetla informacje o dowolnych plikach bibliotek, które nie są używane podczas tworzenia obrazu.|

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Rozwiń **konsolidatora** folderu.

1. Wybierz **wiersza polecenia** stronę właściwości.

1. Dodaj opcję **dodatkowe opcje** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ShowProgress%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)