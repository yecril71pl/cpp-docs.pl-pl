---
title: / PGD (Określ bazę danych dla optymalizacji sterowanych profilem) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ProfileGuidedDatabase
dev_langs:
- C++
helpviewer_keywords:
- -PGD linker option
- /PGD linker option
ms.assetid: 9f312498-493b-461f-886f-92652257e443
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7685f99137a1b599a5f9020fac9e3cae4ba3bc3c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="pgd-specify-database-for-profile-guided-optimizations"></a>/PGD (Określ bazę danych dla optymalizacji sterowanych profilem)

**Opcja /PGD jest przestarzały.** Począwszy od programu Visual Studio 2015, preferowane [opcji/genprofile lub /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) konsolidatora zamiast tego opcje. Ta opcja jest używana do określenia nazwy pliku .pgd używanego przez proces optymalizacji.

## <a name="syntax"></a>Składnia

> **/ PGD:**_filename_

## <a name="argument"></a>Argument

*Nazwa pliku*<br/>
Określa nazwę pliku .pgd, który jest używany do przechowywania informacji na temat uruchomiony program.

## <a name="remarks"></a>Uwagi

Korzystając z przestarzałe [/LTCG:PGINSTRUMENT](../../build/reference/ltcg-link-time-code-generation.md) , należy użyć **/PGD** można określić niestandardowy nazwę lub lokalizację pliku .pgd. Jeśli nie określisz **/PGD**, nazwa podstawowa pliku .pgd jest taka sama jak nazwa pliku wyjściowego (.exe lub .dll) podstawowej i jest tworzony w tym samym katalogu, z którego został wywołany łącza.

Korzystając z przestarzałe **/LTCG:PGOPTIMIZE** , należy użyć **/PGD** opcję, aby określić nazwę pliku .pgd służące do utworzenia zoptymalizowanego obrazu. *Filename* argument powinien być zgodny *filename* określony do **/LTCG:PGINSTRUMENT**.

Aby uzyskać więcej informacji, zobacz [profilowana Optymalizacja](../../build/reference/profile-guided-optimizations.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **optymalizacji** strony właściwości.

1. Modyfikowanie **bazy danych profilu z przewodnikiem** właściwości. Wybierz **OK** Aby zapisać zmiany.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProfileGuidedDatabase%2A>.

## <a name="see-also"></a>Zobacz także

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)<br/>
