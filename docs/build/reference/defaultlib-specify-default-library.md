---
title: / DEFAULTLIB (określ bibliotekę domyślną) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/29/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.DefaultLibraries
- /defaultlib
dev_langs:
- C++
helpviewer_keywords:
- -DEFAULTLIB linker option
- DEFAULTLIB linker option
- /DEFAULTLIB linker option
- libraries, adding to list of
ms.assetid: 6af7ff49-c170-4a13-97e2-2b9ae2de20c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9afcaa0e229ec34ba91b4d60a7a4fa9acec2d7e3
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34569784"
---
# <a name="defaultlib-specify-default-library"></a>/DEFAULTLIB (Określ bibliotekę domyślną)

Określ bibliotekę domyślną wyszukiwania do rozpoznawania odwołań zewnętrznych.

## <a name="syntax"></a>Składnia

> **/ DEFAULTLIB**:_biblioteki_

### <a name="arguments"></a>Argumenty

|Argument|Opis|
|-|-|
*Biblioteka*|Nazwa biblioteki do przeszukania podczas rozpoznawania odwołań zewnętrznych.

## <a name="remarks"></a>Uwagi

**/DEFAULTLIB** opcja dodaje jedną *biblioteki* do listy bibliotek podczas rozpoznawania odwołań wyszukiwania łącza. Określony za pomocą biblioteki **/DEFAULTLIB** przeszukiwany jest po jawnie określona w wierszu polecenia, a przed domyślne biblioteki w .obj — pliki bibliotek.

Gdy jest używany bez argumentów, [/nodefaultlib (Ignoruj wszystkie domyślne biblioteki)](../../build/reference/nodefaultlib-ignore-libraries.md) opcja przesłania wszystkie **/DEFAULTLIB**:*biblioteki* opcje. **/Nodefaultlib**:*biblioteki* opcję zastąpienia **/DEFAULTLIB**:*biblioteki* gdy taki sam *biblioteki*nazwa jest określona w obu.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **wiersza polecenia** strony właściwości.

1. W **dodatkowe opcje**, wprowadź **/DEFAULTLIB**:*biblioteki* opcji dla każdej biblioteki do wyszukiwania. Wybierz **OK** Aby zapisać zmiany.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

- [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)
- [Opcje konsolidatora](../../build/reference/linker-options.md)
