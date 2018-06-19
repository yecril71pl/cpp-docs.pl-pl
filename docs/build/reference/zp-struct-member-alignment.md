---
title: -Zp (wyrównanie członka struktury) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/30/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /zp
- VC.Project.VCCLCompilerTool.StructMemberAlignment
- VC.Project.VCCLWCECompilerTool.StructMemberAlignment
dev_langs:
- C++
helpviewer_keywords:
- Struct Member Alignment compiler option
- Zp compiler option
- /Zp compiler option [C++]
- -Zp compiler option [C++]
ms.assetid: 5242f656-ed9b-48a3-bc73-cfcf3ed2520f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1666da40f748d18c762eae19595692addcdbf78a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380865"
---
# <a name="zp-struct-member-alignment"></a>/Zp (Wyrównanie członka struktury)

Określa, jak elementy członkowskie struktury są pakować do pamięci i umożliwia określenie tej samej pakowania dla wszystkich elementów w module.

## <a name="syntax"></a>Składnia

> **/ZP**[**1**|**2**|**4**|**8** | **16**]

## <a name="remarks"></a>Uwagi

Po określeniu **/Zp**_n_ opcji, każdy element członkowski struktury po zapisaniu pierwszy na rozmiar typ elementu członkowskiego lub *n*-bajtowych granicach (gdzie *n* jest 1, 2, 4, 8 lub 16), w zależności od jest mniejsza.

W poniższej tabeli opisano dostępne pakowania wartości:

|/ZP argumentu|Efekt|
|-|-|
|1|Struktury pakietów przy 1-bajtowych granicach. Taki sam jak **/Zp**.|
|2|Struktury pakietów przy 2-bajtowych granicach.|
|4|Struktury pakietów przy 4-bajtowych granicach.|
|8|Struktury pakietów przy 8-bajtowych granicach (domyślnie).|
|16| Struktury pakietów przy 16-bajtowych granicach.|

Nie należy używać tej opcji, jeśli nie ma wyraźnego związku wymagania.

> [!WARNING]  
> Załóżmy nagłówki C++ w zestawie Windows SDK **/Zp8** pakowania. Jeśli może spowodować uszkodzenie pamięci **/Zp** ustawienie to ulegnie zmianie, korzystając z zestawu Windows SDK nagłówków.

Można również użyć [pakietu](../../preprocessor/pack.md) na pakowanie struktury formantu. Aby uzyskać więcej informacji na temat wyrównania zobacz:

- [align](../../cpp/align-cpp.md)

- [Operator __alignof](../../cpp/alignof-operator.md)

- [__unaligned](../../cpp/unaligned.md)

- [Przykłady wyrównania struktury](../../build/examples-of-structure-alignment.md) (x64 określonych)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **C/C++** > **generowania kodu** strony właściwości.

1. Modyfikowanie **wyrównanie członka struktury** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StructMemberAlignment%2A>.

## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora](../../build/reference/compiler-options.md)   
- [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)
