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
ms.openlocfilehash: b2a6df0f778ba079bffefeeacdad22cb398a529a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820679"
---
# <a name="clrimagetype-specify-type-of-clr-image"></a>/CLRIMAGETYPE (Określenie typu obrazu CLR)

Ustaw typ obrazu CLR w obraz połączony.

## <a name="syntax"></a>Składnia

> **/ CLRIMAGETYPE:**{**IJW**|**CZYSTEJ**|**BEZPIECZNE**|**SAFE32BITPREFERRED**}

## <a name="remarks"></a>Uwagi

Program łączący akceptuje obiekty rodzime i również instrukcje obiektów MSIL, które są kompilowane przy użyciu [/CLR](clr-common-language-runtime-compilation.md). **/CLR: pure** i **/CLR: Safe** opcje kompilatora zostały zaniechane w programie Visual Studio 2015 i nie są obsługiwane w programie Visual Studio 2017. Jeśli przekazano mieszane obiekty w samej kompilacji, możliwość weryfikacji wynikowej pliku wyjściowego jest domyślnie równa najniższego poziomu możliwość weryfikacji modułów wejściowych. Na przykład, jeśli przekażesz obraz macierzysty i obraz w trybie mieszanym (skompilowany przy użyciu **/CLR**), obraz wynikowy będzie obrazem w trybie mieszanym.

Możesz użyć **/clrimagetype** do określenia niższego poziomu możliwość weryfikacji, jeśli jest to, czego potrzebujesz.

Aby uzyskać informacji dotyczących sposobu ustalenia typu obrazu CLR pliku, zobacz [/CLRHEADER](clrheader.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Rozwiń **właściwości konfiguracji** węzła.

1. Rozwiń **konsolidatora** węzła.

1. Wybierz **zaawansowane** stronę właściwości.

1. Modyfikowanie **typu obrazu CLR** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRImageType%2A>.

## <a name="see-also"></a>Zobacz także

- [Odwołania konsolidatora MSVC](linking.md)
- [Opcje konsolidatora MSVC](linker-options.md)
