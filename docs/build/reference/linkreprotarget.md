---
title: /LINKREPROTARGET (nazwa pliku linku Odtwórz)
description: Opcja narzędzia konsolidatora lub biblioteki, aby ustawić nazwę pliku docelowego dla łącza Odtwórz.
ms.date: 09/24/2019
f1_keywords:
- /LINKREPROTARGET
helpviewer_keywords:
- LINKREPROTARGET linker option
- /LINKREPROTARGET linker option
- -LINKREPROTARGET linker option
- linker repro reporting
ms.openlocfilehash: d629c4c2665239d03f38569677fa579b6c8d37e0
ms.sourcegitcommit: a361362354f6ce51eda4ffdb016b81c24cd225cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71712688"
---
# <a name="linkreprotarget-link-repro-file-name"></a>/LINKREPROTARGET (nazwa pliku linku Odtwórz)

Nakazuje narzędziu konsolidatora lub biblioteki Generowanie łącza Odtwórz tylko wtedy, gdy element docelowy ma określoną nazwę pliku.

## <a name="syntax"></a>Składnia

> **/LINKREPROTARGET:** _Nazwa pliku_

### <a name="arguments"></a>Argumenty

**/LINKREPROTARGET:** _Nazwa pliku_\
Nazwa docelowego pliku do filtrowania. Link Odtwórz jest generowany tylko wtedy, gdy nazwany plik jest docelowym wyjściem. Nazwy plików zawierające spacje muszą być ujęte w podwójne cudzysłowy. Nazwa pliku powinna zawierać nazwę podstawową i rozszerzenie, ale nie ścieżkę.

## <a name="remarks"></a>Uwagi

Opcja **/LINKREPROTARGET** służy do określania nazwy pliku docelowego w celu wygenerowania *linku Odtwórz* dla. Link Odtwórz to zestaw artefaktów kompilacji, które umożliwiają firmie Microsoft odtwarzanie problemu występującego w czasie konsolidacji lub podczas operacji biblioteki. Narzędzie konsolidatora lub biblioteka tworzy łącze Odtwórz w przypadku określenia opcji [/LINKREPRO](linkrepro.md) lub ustawienia zmiennej środowiskowej `link_repro` w środowisku kompilacji wiersza polecenia.

Opcja **/LINKREPROTARGET** jest przydatna w złożonych kompilacjach, które wywołują narzędzia konsolidatora lub biblioteki więcej niż raz. Umożliwia określenie konkretnego elementu docelowego dla linku Odtwórz, takiego jak *plik. dll*. Umożliwia generowanie Odtwórz linku tylko wtedy, gdy narzędzie tworzy określony plik.

Aby uzyskać więcej informacji na temat sposobu i czasu tworzenia linku Odtwórz, zobacz sekcję dotyczącą [linków](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md#link-repros) [Reports, aby zgłosić problem z zestawem narzędzi firmy Microsoft C++ ](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md).

Aby opcja **/LINKREPROTARGET** działała, należy ustawić opcje **/LINKREPRO** i [/out](out-output-file-name.md) .

**/LINKREPROTARGET** jest dostępna od wersji 16,1 programu Visual Studio 2019.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Właściwości konfiguracji** > **konsolidator** >  Strona właściwości**wiersza polecenia** .

1. Wprowadź opcję **/LINKREPROTARGET:** _File-Name_ w polu **dodatkowe opcje** . Wybierz **przycisk OK** , aby zastosować zmianę.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Odwołanie konsolidatora MSVC](linking.md)\
[MSVC Opcje konsolidatora](linker-options.md)\
[/LINKREPRO](linkrepro.md)
