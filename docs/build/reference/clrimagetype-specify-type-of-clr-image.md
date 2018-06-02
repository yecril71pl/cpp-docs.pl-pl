---
title: / CLRIMAGETYPE (określenie typu obrazu CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /CLRIMAGETYPE
- VC.Project.VCLinkerTool.CLRImageType
dev_langs:
- C++
helpviewer_keywords:
- /CLRIMAGETYPE linker option
- -CLRIMAGETYPE linker option
ms.assetid: 04c60ee6-9dd7-4391-bc03-6926ad0fa116
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b5efb2e73e854591be7134753cec21a708fff3e5
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34705013"
---
# <a name="clrimagetype-specify-type-of-clr-image"></a>/CLRIMAGETYPE (Określenie typu obrazu CLR)

Ustaw typ obrazu CLR w połączonego obrazu.

## <a name="syntax"></a>Składnia

> **/ CLRIMAGETYPE:**{**IJW**|**CZYSTEJ**|**BEZPIECZNE**|**SAFE32BITPREFERRED**}

## <a name="remarks"></a>Uwagi

Konsolidator akceptuje obiektów macierzystych i również MSIL obiekty, które są kompilowane przy użyciu [/CLR](../../build/reference/clr-common-language-runtime-compilation.md). **/CLR: pure** i **/CLR: Safe** — opcje kompilatora zostały uznane za przestarzałe w programie Visual Studio 2015 i nie są obsługiwane w programie Visual Studio 2017 r. Gdy mieszanych obiektów w tej samej kompilacji są przekazywane, możliwość weryfikacji wynikowego pliku wyjściowego jest, domyślnie równa najniższa możliwość wprowadzania modułów weryfikacji. Na przykład w przypadku przekazania obrazu macierzystego i obraz trybu mieszanego (skompilowana przy użyciu **/CLR**), obraz wynikowy będzie obrazu w trybie mieszanym.

Można użyć **clrimagetype** do określenia niższej możliwość weryfikacji, jeżeli jest to, co jest potrzebne.

Aby uzyskać informacje o tym, jak można ustalić typu obrazu CLR pliku, zobacz [/CLRHEADER](../../build/reference/clrheader.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Rozwiń węzeł **właściwości konfiguracji** węzła.

1. Rozwiń węzeł **konsolidatora** węzła.

1. Wybierz **zaawansowane** strony właściwości.

1. Modyfikowanie **typu obrazu CLR** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRImageType%2A>.

## <a name="see-also"></a>Zobacz także

- [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)
- [Opcje konsolidatora](../../build/reference/linker-options.md)
