---
title: /PGD (Określ bazę danych dla optymalizacji sterowanych profilem)
ms.date: 03/14/2018
f1_keywords:
- VC.Project.VCLinkerTool.ProfileGuidedDatabase
helpviewer_keywords:
- -PGD linker option
- /PGD linker option
ms.assetid: 9f312498-493b-461f-886f-92652257e443
ms.openlocfilehash: e1d7c9fcb94a9351ce94b66e04b4bfc523248f4e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319801"
---
# <a name="pgd-specify-database-for-profile-guided-optimizations"></a>/PGD (Określ bazę danych dla optymalizacji sterowanych profilem)

**Opcja /PGD jest przestarzały.** Począwszy od programu Visual Studio 2015 Preferuj [przełączników/genprofile i/fastgenprofile](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) zamiast tego opcje konsolidatora. Ta opcja jest używana do określenia nazwy pliku .pgd używany przez proces optymalizacji sterowanej profilem.

## <a name="syntax"></a>Składnia

> **/ PGD:**_nazwy pliku_

## <a name="argument"></a>Argument

*Nazwa pliku*<br/>
Określa nazwę pliku .pgd, który jest używany do przechowywania informacji na temat uruchomionego programu.

## <a name="remarks"></a>Uwagi

Korzystając z przestarzałego [pginstrument](ltcg-link-time-code-generation.md) opcji, należy użyć **/PGD** do określenia niedomyślną nazwą lub lokalizacją pliku .pgd. Jeśli nie określisz **/PGD**, nazwa podstawowa pliku .pgd jest taka sama jak nazwa pliku wyjściowego (.exe lub .dll) podstawowej i jest tworzony w tym samym katalogu, z którego wywołano łącze.

Korzystając z przestarzałego **/LTCG:PGOPTIMIZE** opcji, należy użyć **/PGD** opcję, aby określić nazwę pliku .pgd można użyć do utworzenia zoptymalizowanego obrazu. *Filename* argument powinien być zgodny *filename* określony do **pginstrument**.

Aby uzyskać więcej informacji, zobacz [optymalizacje Profile-Guided](../profile-guided-optimizations.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **optymalizacji** stronę właściwości.

1. Modyfikowanie **profilowej bazie danych z przewodnikiem** właściwości. Wybierz **OK** Aby zapisać zmiany.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProfileGuidedDatabase%2A>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)<br/>
