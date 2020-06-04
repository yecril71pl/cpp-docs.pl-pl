---
title: /CETCOMPAT (zgodny ze stosem w tle)
ms.date: 02/19/2019
f1_keywords:
- /CETCOMPAT
helpviewer_keywords:
- /CETCOMPAT linker option
- /CETCOMPAT
ms.openlocfilehash: 2c807d91d69b967fd62e01a077711dede5f55c44
ms.sourcegitcommit: 7e011c68ca7547469544fac87001a33a37e1792e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84421304"
---
# <a name="cetcompat-cet-shadow-stack-compatible"></a>/CETCOMPAT (zgodny ze stosem w tle)

Określa, czy obraz wykonywalny ma być oznaczany jako zgodny z technologią wymuszania przepływu sterowania (CET).

## <a name="syntax"></a>Składnia

> **/CETCOMPAT** \[ **: Nie**]

## <a name="arguments"></a>Argumenty

**ZNALEZIONO**<br/>
Określa, że plik wykonywalny nie powinien być oznaczony jako zgodny z atrybutem "CET Shadow Stack".

## <a name="remarks"></a>Uwagi

Stos kontroli sterowania przepływem (CET) to funkcja procesora komputerowego, która zapewnia możliwość obrony przed atakami polegającymi na programowaniu opartym na oprogramowaniu ROP. Aby uzyskać więcej informacji, zobacz temat [Technologia wymuszania przepływu sterowania przez firmę Intel](https://software.intel.com/sites/default/files/managed/4d/2a/control-flow-enforcement-technology-preview.pdf).

Opcja konsolidatora **/CETCOMPAT** nakazuje konsolidatorowi oznaczenie plików binarnych jako niezgodnych ze stosem w tle. **/CETCOMPAT: nie** oznacza elementów binarnych jako niezgodnych z stosem w tle w trybie CET. Jeśli obie opcje są określone w wierszu polecenia, zostanie użyta Ostatnia z nich. Ten przełącznik jest obecnie stosowany tylko do architektur x86 i x64.

Opcja **/CETCOMPAT** jest dostępna, zaczynając od zestawu narzędzi Visual Studio 2019 Preview 3.

### <a name="to-set-the-cetcompat-linker-option-in-visual-studio"></a>Aby ustawić opcję konsolidatora/CETCOMPAT w programie Visual Studio

1. Otwórz okno dialogowe **strony właściwości** dla projektu. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../working-with-project-properties.md).

1. Wybierz stronę właściwości **Konfiguracja**  >  **konsolidator**  >  **Zaawansowane** właściwości.

1. Wybierz właściwość CET, która jest **zgodna ze stosem** .

1. W kontrolce menu rozwijanego wybierz pozycję **tak (/CETCOMPAT)** , aby włączyć metadane kontynuacji eh, lub pozycję **nie (/CETCOMPAT: No)** , aby ją wyłączyć.


### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

Ta opcja nie ma programowego odpowiednika.

## <a name="see-also"></a>Zobacz też

[Opcje konsolidatora](linker-options.md)
