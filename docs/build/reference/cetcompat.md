---
title: / CETCOMPAT (zgodny z CET cień stosu)
ms.date: 02/19/2019
f1_keywords:
- /CETCOMPAT
helpviewer_keywords:
- /CETCOMPAT linker option
- /CETCOMPAT
ms.openlocfilehash: 0ed5d9d4f9f4f4dc5cd4fc19df4179e86e430187
ms.sourcegitcommit: 42e65c171aaa17a15c20b155d22e3378e27b4642
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2019
ms.locfileid: "58356018"
---
# <a name="cetcompat-cet-shadow-stack-compatible"></a>/ CETCOMPAT (zgodny z CET cień stosu)

Określa, czy należy oznaczyć obrazu wykonywalnego jako niezgodny z stos cieni technologia wymuszania (CET) przepływ sterowania.

## <a name="syntax"></a>Składnia

> **/ CETCOMPAT**\[**: NO**]

## <a name="arguments"></a>Argumenty

**BRAK**<br/>
Określa, że plik wykonywalny nie powinien być oznaczony zgodny z CET cień stosu.

## <a name="remarks"></a>Uwagi

Stos cieni technologia wymuszania (CET) przepływu sterowania jest funkcją procesora komputera, która zapewnia możliwości do obrony przed zwracanym programowanie zorientowane na obiekty (w prawym GÓRNYM) na podstawie atakami złośliwego oprogramowania. Aby uzyskać więcej informacji, zobacz [Intel przepływ sterowania wymuszania Technology Preview](https://software.intel.com/sites/default/files/managed/4d/2a/control-flow-enforcement-technology-preview.pdf).

**/CETCOMPAT** — opcja konsolidatora informuje konsolidator, aby oznaczyć danych binarnych jako zgodnego z CET cień stosu. **/CETCOMPAT:No** oznacza plik binarny, co nie jest zgodna z CET cień stosu. Jeśli obie opcje są określone w wierszu polecenia, określony ostatni z nich jest używany. Ten przełącznik dotyczy aktualnie tylko x86 i x64 architektury.

**/CETCOMPAT** opcja jest dostępna, począwszy od zestawu narzędzi Visual Studio 3 (wersja zapoznawcza) 2019 r.

### <a name="to-set-the-cetcompat-linker-option-in-visual-studio"></a>Aby ustawić opcję konsolidatora /CETCOMPAT w programie Visual Studio

1. Otwórz **stron właściwości** okno dialogowe dla projektu. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **wiersza polecenia** stronę właściwości.

1. W **dodatkowe opcje** Dodaj **/CETCOMPAT** lub **/CETCOMPAT:NO** , a następnie wybierz **OK** lub **Zastosuj**Aby zapisać zmiany.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

Ta opcja nie ma programowy odpowiednik.

## <a name="see-also"></a>Zobacz także

[Opcje konsolidatora](linker-options.md)
