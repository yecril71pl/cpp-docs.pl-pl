---
title: / CETCOMPAT (zgodny z technologia wymuszania przepływu sterowania)
ms.date: 02/19/2019
f1_keywords:
- /CETCOMPAT
helpviewer_keywords:
- /CETCOMPAT linker option
- /CETCOMPAT
ms.openlocfilehash: 1a01dd45667f64dbcbe11acaf1180835bd0d6e31
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809850"
---
# <a name="cetcompat-control-flow-enforcement-technology-compatible"></a>/ CETCOMPAT (zgodny z technologia wymuszania przepływu sterowania)

Określa, czy należy oznaczyć obrazu wykonywalnego jako niezgodny z technologia wymuszania przepływu sterowania (CET).

## <a name="syntax"></a>Składnia

> **/ CETCOMPAT**\[**: NO**]

## <a name="arguments"></a>Argumenty

**BRAK**<br/>
Określa, że plik wykonywalny nie powinien być oznaczony zgodny z CET.

## <a name="remarks"></a>Uwagi

Technologia wymuszania przepływu sterowania (CET) jest funkcją procesora komputera, która oferuje możliwości do obrony przed niektórych rodzajów ataków złośliwego oprogramowania. Aby uzyskać więcej informacji, zobacz [Intel przepływ sterowania wymuszania Technology Preview](https://software.intel.com/sites/default/files/managed/4d/2a/control-flow-enforcement-technology-preview.pdf).

**/CETCOMPAT** — opcja konsolidatora informuje konsolidator, aby oznaczyć danych binarnych jako CET zgodny. **/CETCOMPAT:No** oznacza plik binarny, co nie jest zgodna z CET. Jeśli obie opcje są określone w wierszu polecenia, określony ostatni z nich jest używany. Ten przełącznik dotyczy aktualnie tylko x86 i x64 architektury.

**/CETCOMPAT** opcja jest dostępna, począwszy od zestawu narzędzi Visual Studio 3 (wersja zapoznawcza) 2019 r.

### <a name="to-set-the-cetcompat-linker-option-in-visual-studio"></a>Aby ustawić opcję konsolidatora /CETCOMPAT w programie Visual Studio

1. Otwórz **stron właściwości** okno dialogowe dla projektu. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **wiersza polecenia** stronę właściwości.

1. W **dodatkowe opcje** Dodaj **/CETCOMPAT** lub **/CETCOMPAT:NO** , a następnie wybierz **OK** lub **Zastosuj**Aby zapisać zmiany.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

Ta opcja nie ma programowy odpowiednik.

## <a name="see-also"></a>Zobacz także

[Opcje konsolidatora](linker-options.md)
