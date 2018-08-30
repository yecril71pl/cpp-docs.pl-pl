---
title: / SECTION (Określ atrybuty sekcji) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/29/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /section
dev_langs:
- C++
helpviewer_keywords:
- SECTION linker option
- -SECTION linker option
- section attributes
- /SECTION linker option
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1f052d8acaceee88b6b9a727e176666180b1bb9d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43214183"
---
# <a name="section-specify-section-attributes"></a>/SECTION (Określ atrybuty sekcji)

> **/ SECTION:**_nazwa_, [[**!**] {**DEKPRSW**}] [**, ALIGN =**_numer_]

## <a name="remarks"></a>Uwagi

**/SECTION** opcji zmienia atrybuty sekcji, zastępując atrybuty ustawione, gdy plik .obj sekcji został skompilowany.

A *sekcji* w przenośnym pliku wykonywalnym (PE) pliku jest o nazwie, ciągłym bloku pamięci, która zawiera kod lub danych. Niektóre sekcje zawierają kod lub dane, które program zadeklarowane ale korzysta z bezpośrednio, natomiast pozostałe sekcje danych utworzone za pomocą konsolidatora i biblioteki menedżera (lib.exe) zawierają informacje niezbędne do systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [formatu PE](/windows/desktop/Debug/pe-format).

Określ dwukropek (:) i sekcję *nazwa*. *Nazwa* jest uwzględniana wielkość liter.

Nie należy używać następujących nazw, ponieważ powodują konfliktów z nazwami standardowych. Na przykład .sdata jest używany na platformach RISC:

- .arch

- .BSS

- .Data

- .edata

- .idata

- .PData

- .rdata

- .reloc

- rsrc

- .sbss

- .sdata

- .srdata

- .Text

- .xdata

Określ jeden lub więcej atrybutów w sekcji. Znaków atrybutu, wymienione poniżej pod warunkiem jest uwzględniana wielkość liter. Należy określić wszystkie atrybuty, które chcesz sekcji, aby mieć; znak pominięty atrybutu powoduje, że ten bit atrybutu do wyłączenia. Jeśli nie określisz R, W lub E, istniejące odczytu, zapisu lub wykonywalny nadal będzie w stanie niezmieniony.

Aby odwrócić atrybutu, należy poprzedzić jej znakiem wykrzyknika (!). W tej tabeli przedstawiono znaczenie znaków atrybutu:

|Znak|Atrybut|Znaczenie|
|---------------|---------------|-------------|
|E|Wykonywanie|Sekcja jest wykonywalny|
|R|Odczyt|Zezwala na operacje odczytu danych|
|W|Write|Umożliwia wykonywanie operacji zapisu na danych|
|S|Shared|Udostępnia sekcji między wszystkie procesy, które ładują obrazu|
|D|Discardable|Oznacza sekcji discardable|
|K|Podlega buforowaniu|Oznacza sekcji nie podlega buforowaniu|
|P|Stronicowanej|Oznacza sekcji nie stronicowanej|

K i P są w tej flagi sekcji, które odnoszą się do nich są używane w tym sensie, ujemna. Jeśli należy określić jeden z nich w sekcji .text za pomocą **/SECTION:.text, K** opcji, nie ma żadnej różnicy w sekcji flagi, po uruchomieniu [DUMPBIN](../../build/reference/dumpbin-options.md) z [/HEADERS](../../build/reference/headers.md)opcji; sekcja już niejawnie był buforowany. Nie można usunąć domyślnego, określ **/SECTION:.text,! K** zamiast tego. DUMPBIN, co spowoduje wyświetlenie właściwości sekcji, w tym "Nie pamięci podręcznej."

Do sekcji w pliku PE, który nie ma E, R lub ustaw W jest prawdopodobnie nieprawidłowy.

**ALIGN =**_numer_ argument pozwala określić wartość wyrównania dla określonej sekcji. _Numer_ argument w bajtach i musi być potęgą liczby dwa. Zobacz [/ALIGN](../../build/reference/align-section-alignment.md) Aby uzyskać więcej informacji.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1.  Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **wiersza polecenia** stronę właściwości.

1. Wpisz opcje w **dodatkowe opcje** pole. Wybierz **OK** lub **Zastosuj** do zastosowania zmiany.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)  
[Opcje konsolidatora](../../build/reference/linker-options.md)  
