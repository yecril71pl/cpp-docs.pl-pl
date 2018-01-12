---
title: "/ SECTION (Określ atrybuty sekcji) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 12/29/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /section
dev_langs: C++
helpviewer_keywords:
- SECTION linker option
- -SECTION linker option
- section attributes
- /SECTION linker option
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aa214c7efeeee595300204df900a333258052772
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="section-specify-section-attributes"></a>/SECTION (Określ atrybuty sekcji)

> **/ SECTION:**_nazwa_, [[**!**] {**DEKPRSW**}] [**, ALIGN =**_numer_]

## <a name="remarks"></a>Uwagi

**/SECTION** opcja zmienia atrybuty sekcji, zastępując zestaw atrybutów, gdy plik .obj sekcji został skompilowany.

A *sekcji* w przenośnym pliku wykonywalnym (PE) pliku jest nazwane ciągły blok pamięci, który zawiera kod lub dane. Niektóre sekcje zawierają kod lub dane, które program zadeklarowany i używa bezpośrednio, natomiast pozostałe sekcje zasad zachowania danych są tworzone przez konsolidatora i biblioteki menedżera (lib.exe) i zawierają informacje niezbędne do tego systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [formatu PE](https://msdn.microsoft.com/library/windows/desktop/ms680547).

Określ dwukropkiem (:) i sekcję *nazwa*. *Nazwa* uwzględniana jest wielkość liter.

Nie należy używać następujących nazw, jak powodują konfliktów z już standardowe nazwy. Na przykład .sdata jest używana na platformach RISC:

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

Określ jeden lub więcej atrybutów dla sekcji. Znaki atrybutu, wymienione poniżej, nie jest uwzględniana. Należy określić wszystkie atrybuty, które mają sekcji, aby mieć; znak pominięty atrybut powoduje, że tego atrybutu bit do wyłączenia. Jeśli nie określisz R, P lub E, istniejące odczytu, zapisu lub pliku wykonywalnego stan jest zmieniany.

Aby odwrócić atrybutu, należy poprzedzić jej znak symbolem wykrzyknika (!). W tej tabeli przedstawiono znaczenie znaków atrybutu:

|Znak|Atrybut|Znaczenie|
|---------------|---------------|-------------|
|E|Wykonanie|Sekcja jest pliku wykonywalnego|
|R|Odczyt|Zezwala na operacje odczytu danych|
|W|Write|Zezwala na wykonywanie operacji zapisu na danych|
|S|Shared|Udostępnia sekcji między wszystkie procesy, które ładują obrazu|
|D|Discardable|Oznacza sekcji jako discardable|
|K|Buforowalnej|Oznacza sekcji jako nie buforowalnej|
|P|Stronicowalnej|Oznacza sekcji jako nie stronicowalnej|

K i P są w tej flagi sekcji, które odnoszą się do nich są używane w tym sensie, ujemne. Jeśli określisz jeden z nich w sekcji .text za pomocą **/SECTION:.text, K** opcji, nie ma żadnej różnicy w sekcji flagi, po uruchomieniu [DUMPBIN](../../build/reference/dumpbin-options.md) z [/HEADERS](../../build/reference/headers.md)opcję; sekcja już niejawnie był buforowany. Nie można usunąć domyślnego, określ **/SECTION:.text,! K** zamiast tego. DUMPBIN ujawnia właściwości sekcji, w tym "Niebuforowane."

Sekcja w pliku PE, które nie ma E, R lub ustawiona W jest prawdopodobnie nieprawidłowy.

**ALIGN =**_numer_ argument pozwala określić wartość wyrównania dla określonej sekcji. _Numer_ argument w bajtach i musi być potęgą liczby dwa. Zobacz [/ALIGN](../../build/reference/align-section-alignment.md) Aby uzyskać więcej informacji.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **wiersza polecenia** strony właściwości.

1. Wybierz opcję w **dodatkowe opcje** pole. Wybierz **OK** lub **Zastosuj** do zastosowania zmiany.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)  
[Opcje konsolidatora](../../build/reference/linker-options.md)  
