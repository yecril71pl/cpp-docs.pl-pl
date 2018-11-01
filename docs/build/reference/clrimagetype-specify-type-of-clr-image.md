---
title: /CLRIMAGETYPE (Określenie typu obrazu CLR)
ms.date: 11/04/2016
f1_keywords:
- /CLRIMAGETYPE
- VC.Project.VCLinkerTool.CLRImageType
helpviewer_keywords:
- /CLRIMAGETYPE linker option
- -CLRIMAGETYPE linker option
ms.assetid: 04c60ee6-9dd7-4391-bc03-6926ad0fa116
ms.openlocfilehash: c4cdb9a9ac3376762d6aa40fd4c13abbdc7b5487
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461636"
---
# <a name="clrimagetype-specify-type-of-clr-image"></a>/CLRIMAGETYPE (Określenie typu obrazu CLR)

Ustaw typ obrazu CLR w obraz połączony.

## <a name="syntax"></a>Składnia

> **/ CLRIMAGETYPE:**{**IJW**|**CZYSTEJ**|**BEZPIECZNE**|**SAFE32BITPREFERRED**}

## <a name="remarks"></a>Uwagi

Program łączący akceptuje obiekty rodzime i również instrukcje obiektów MSIL, które są kompilowane przy użyciu [/CLR](../../build/reference/clr-common-language-runtime-compilation.md). **/CLR: pure** i **/CLR: Safe** opcje kompilatora zostały zaniechane w programie Visual Studio 2015 i nie są obsługiwane w programie Visual Studio 2017. Jeśli przekazano mieszane obiekty w samej kompilacji, możliwość weryfikacji wynikowej pliku wyjściowego jest domyślnie równa najniższego poziomu możliwość weryfikacji modułów wejściowych. Na przykład, jeśli przekażesz obraz macierzysty i obraz w trybie mieszanym (skompilowany przy użyciu **/CLR**), obraz wynikowy będzie obrazem w trybie mieszanym.

Możesz użyć **/clrimagetype** do określenia niższego poziomu możliwość weryfikacji, jeśli jest to, czego potrzebujesz.

Aby uzyskać informacji dotyczących sposobu ustalenia typu obrazu CLR pliku, zobacz [/CLRHEADER](../../build/reference/clrheader.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Rozwiń **właściwości konfiguracji** węzła.

1. Rozwiń **konsolidatora** węzła.

1. Wybierz **zaawansowane** stronę właściwości.

1. Modyfikowanie **typu obrazu CLR** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRImageType%2A>.

## <a name="see-also"></a>Zobacz także

- [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)
- [Opcje konsolidatora](../../build/reference/linker-options.md)
