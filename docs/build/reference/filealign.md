---
title: / FILEALIGN (Wyrównaj sekcje w plikach)
ms.date: 10/23/2017
f1_keywords:
- /filealign
helpviewer_keywords:
- linker align sections
- /FILEALIGN linker option
- -FILEALIGN linker option
- FILEALIGN linker option
ms.assetid: c1017a35-8d71-4ad9-934b-a3e3ea037fa0
ms.openlocfilehash: 43cfdd6efb163013d05877e91c8375eb592295a9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271154"
---
# <a name="filealign-align-sections-in-files"></a>/ FILEALIGN (Wyrównaj sekcje w plikach)

**/Filealign** — opcja konsolidatora umożliwia określanie wyrównania sekcji zapisywane do pliku danych wyjściowych jako wielokrotności określonego rozmiaru.

## <a name="syntax"></a>Składnia

> __/ FILEALIGN:__*rozmiar*

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
Wyrównanie sekcji rozmiar w bajtach, które musi być potęgą liczby dwa.

## <a name="remarks"></a>Uwagi

**/Filealign** opcji powoduje, że konsolidator wyrównanie każdej sekcji w pliku danych wyjściowych na granicy, która jest wielokrotnością liczby *rozmiar* wartość. Domyślnie konsolidator nie używa o rozmiarze stałym wyrównania.

**/Filealign** opcji można wprowadzić bardziej efektywne wykorzystanie dysku lub aby strona ładuje z dysku szybciej. Mniejszy rozmiar sekcji może być przydatne w przypadku aplikacji działających w mniejszych urządzeniach lub zachować mniejsze pliki do pobrania. Wyrównanie sekcji na dysku nie ma wpływu na wyrównania w pamięci.

Użyj [DUMPBIN](dumpbin-reference.md) Aby wyświetlić informacje o sekcji w pliku danych wyjściowych.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **wiersza polecenia** — strona właściwości w **konsolidatora** folderu.

1. Wpisz opcje nazwy **/filealign:** i rozmiar w **dodatkowe opcje** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
