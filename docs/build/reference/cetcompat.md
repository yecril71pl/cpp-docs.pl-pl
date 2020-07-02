---
title: /CETCOMPAT (zgodny ze stosem w tle)
ms.date: 06/30/2020
f1_keywords:
- /CETCOMPAT
helpviewer_keywords:
- /CETCOMPAT linker option
- /CETCOMPAT
ms.openlocfilehash: 35078ac9e6177e34562db14b30f4ef8f987d98bc
ms.sourcegitcommit: 83ea5df40917885e261089b103d5de3660314104
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85813566"
---
# <a name="cetcompat-cet-shadow-stack-compatible"></a>/CETCOMPAT (zgodny ze stosem w tle)

Określa, czy obraz wykonywalny ma być oznaczany jako zgodny z technologią wymuszania przepływu sterowania (CET).

## <a name="syntax"></a>Składnia

> **`/CETCOMPAT`**\
> **`/CETCOMPAT:NO`**

## <a name="arguments"></a>Argumenty

**`NO`**<br/>
Określa, że plik wykonywalny nie powinien być oznaczony jako zgodny z opcją CET stosu cienia.

## <a name="remarks"></a>Uwagi

Sterowanie przepływem sterowania — Technologia wymuszania przepływu (CET) to funkcja procesora komputerowego, która zapewnia możliwość obrony przed atakami wykorzystującymi oprogramowanie wykorzystujące programowanie (ROP). Aby uzyskać więcej informacji, zobacz temat [Technologia wymuszania przepływu sterowania przez firmę Intel](https://software.intel.com/sites/default/files/managed/4d/2a/control-flow-enforcement-technology-preview.pdf).

**`/CETCOMPAT`** Opcja konsolidatora nakazuje konsolidatorowi oznaczenie pliku binarnego jako niezgodnego ze stosem w tle. **`/CETCOMPAT:NO`** oznacza plik binarny jako niezgodny ze stosem w tle w trybie CET. Jeśli obie opcje są określone w wierszu polecenia, zostanie użyta Ostatnia z nich. Ten przełącznik jest obecnie stosowany tylko do architektur x86 i x64.

Ta **`/CETCOMPAT`** opcja jest dostępna, zaczynając od programu Visual Studio 2019.

### <a name="to-set-the-cetcompat-linker-option-in-visual-studio"></a>Aby ustawić `/CETCOMPAT` opcję konsolidatora w programie Visual Studio

Począwszy od programu Visual Studio 2019 w wersji 16,7:

1. Otwórz okno dialogowe **strony właściwości** dla projektu. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../working-with-project-properties.md).

1. Wybierz stronę właściwości **Konfiguracja**  >  **konsolidator**  >  **Zaawansowane** właściwości.

1. Wybierz właściwość CET, która jest **zgodna ze stosem** .

1. W kontrolce menu rozwijanego wybierz opcję **`Yes (/CETCOMPAT)`** włączenia metadanych kontynuacji EH lub **`No (/CETCOMPAT:NO)`** wyłączania.

W poprzednich wersjach programu Visual Studio 2019:

1. Otwórz okno dialogowe **strony właściwości** dla projektu. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../working-with-project-properties.md).

1. Wybierz stronę właściwości **Konfiguracja właściwości**  >  **Linker**  >  **wiersza polecenia** konsolidatora.

1. W obszarze **Opcje dodatkowe** Edytuj kontrolkę Dodaj, *`/CETCOMPAT`* Aby włączyć metadane kontynuacji EH lub *`/CETCOMPAT:NO`* Aby jawnie ją wyłączyć.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

Ta opcja nie ma programowego odpowiednika.

## <a name="see-also"></a>Zobacz także

[Opcje konsolidatora](linker-options.md)
