---
title: "/ FILEALIGN (wyrównanie sekcji w plikach) | Dokumentacja firmy Microsoft"
ms.date: 10/23/2017
ms.technology:
- cpp-tools
ms.topic: article
f1_keywords:
- /filealign
dev_langs:
- C++
helpviewer_keywords:
- linker align sections
- /FILEALIGN linker option
- -FILEALIGN linker option
- FILEALIGN linker option
ms.assetid: c1017a35-8d71-4ad9-934b-a3e3ea037fa0
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 753f6c5fade4211654246aec19af60c60706d7ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="filealign-align-sections-in-files"></a>/ FILEALIGN (wyrównanie sekcji w plikach)

**/Filealign** — opcja konsolidatora umożliwia określanie wyrównania sekcji zapisywane do pliku wyjściowego wielokrotnością określonego rozmiaru.

## <a name="syntax"></a>Składnia

> __/ FILEALIGN:__*rozmiaru*

### <a name="parameters"></a>Parametry

*rozmiar*  
Wyrównanie sekcji rozmiar w bajtach, które musi być potęgą liczby dwa.

## <a name="remarks"></a>Uwagi

**/Filealign** opcja powoduje, że konsolidator, aby wyrównać każdej sekcji w pliku wyjściowym w granicach jest wielokrotnością liczby *rozmiar* wartość. Domyślnie konsolidator nie używa o rozmiarze stałym wyrównania.

**/Filealign** opcji można wprowadzić bardziej efektywne wykorzystanie dysku lub aby strona ładuje z dysku szybciej. Mniejszy rozmiar sekcji może być przydatne w przypadku aplikacji uruchamianych na mniejsze urządzenia lub zachować mniejsze pliki do pobrania. Wyrównanie sekcji na dysku nie ma wpływu na wyrównania w pamięci.

Użyj [DUMPBIN](dumpbin-reference.md) Aby wyświetlić informacje o sekcji w pliku danych wyjściowych.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **wiersza polecenia** stronę właściwości w **konsolidatora** folderu.

1. Wpisz nazwę opcji **/filealign:** i rozmiar w **dodatkowe opcje** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
[Opcje konsolidatora](../../build/reference/linker-options.md)