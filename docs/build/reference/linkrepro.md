---
title: /LINKREPRO (Nazwa linku Odtwórz Directory)
description: Opcja narzędzia konsolidatora lub biblioteki służąca do ustawiania katalogu dla łącza Odtwórz.
ms.date: 09/24/2019
f1_keywords:
- /LINKREPRO
helpviewer_keywords:
- LINKREPRO linker option
- /LINKREPRO linker option
- -LINKREPRO linker option
- linker repro reporting
ms.openlocfilehash: d81fb529cdbb0741c6dff58032dad97df89b4d4f
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2019
ms.locfileid: "71686853"
---
# <a name="linkrepro-link-repro-directory-name"></a>/LINKREPRO (Nazwa linku Odtwórz Directory)

Informuje konsolidator lub narzędzie biblioteki w celu wygenerowania linku Odtwórz w określonym katalogu.

## <a name="syntax"></a>Składnia

> **/LINKREPRO:** _Nazwa katalogu_

### <a name="arguments"></a>Argumenty

**/LINKREPRO:** _Nazwa katalogu_\
Katalog określony przez użytkownika, w którym ma zostać zapisane łącze Odtwórz. Nazwy katalogów zawierające spacje muszą być ujęte w podwójne cudzysłowy.

## <a name="remarks"></a>Uwagi

Opcja **/LINKREPRO** służy do tworzenia *linku Odtwórz*. Jest to zestaw artefaktów kompilacji, który umożliwia firmie Microsoft odtwarzanie problemu występującego w czasie konsolidacji lub podczas operacji biblioteki. Jest to przydatne w przypadku problemów, takich jak awaria zaplecza obejmująca generowanie kodu w czasie konsolidacji (LTCG), błąd konsolidatora LNK1000 lub awarię konsolidatora. Narzędzie tworzy łącze Odtwórz podczas określania opcji konsolidatora **/LINKREPRO** lub w przypadku ustawienia zmiennej środowiskowej `link_repro` w środowisku kompilacji wiersza polecenia. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [linków](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md#link-repros) [Reports, aby zgłosić problem z zestawem narzędzi firmy Microsoft C++ ](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md).

Opcja konsolidatora **/LINKREPRO** i zmienna środowiskowa `link_repro` wymagają określenia katalogu wyjściowego dla linku Odtwórz. W wierszu polecenia lub w środowisku IDE określ katalog przy użyciu opcji **/LINKREPRO:** _Directory-Name_ . Określona _Nazwa katalogu_ może być ścieżką bezwzględną lub względną, ale katalog musi istnieć. Opcja wiersza polecenia zastępuje wszystkie wartości katalogowe ustawione w zmiennej środowiskowej `link_repro`.

Aby dowiedzieć się, jak ograniczyć generowanie Odtwórz łącza do określonej nazwy pliku docelowego, zobacz opcję [/LINKREPROTARGET](linkreprotarget.md) . Tej opcji można użyć, aby określić konkretny element docelowy do wygenerowania linku Odtwórz dla. Jest to przydatne w złożonych kompilacjach, które wywołują narzędzia konsolidatora lub biblioteki więcej niż raz.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Właściwości konfiguracji** > **konsolidator** >  Strona właściwości**wiersza polecenia** .

1. Wprowadź opcję **/LINKREPRO:** _Directory-Name_ w polu **dodatkowe opcje** . Określona wartość _nazwy katalogu_ musi istnieć. Wybierz **przycisk OK** , aby zastosować zmianę.

Po wygenerowaniu Odtwórz linku ponownie otwórz Tę stronę właściwości, aby usunąć opcję **/LINKREPRO** z kompilacji.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Odwołanie konsolidatora MSVC](linking.md)\
[MSVC Opcje konsolidatora](linker-options.md)\
[/LINKREPROTARGET](linkreprotarget.md)
