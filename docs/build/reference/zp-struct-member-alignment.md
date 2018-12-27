---
title: /Zp (Wyrównanie członka struktury)
ms.date: 12/17/2018
f1_keywords:
- /zp
- VC.Project.VCCLCompilerTool.StructMemberAlignment
- VC.Project.VCCLWCECompilerTool.StructMemberAlignment
helpviewer_keywords:
- Struct Member Alignment compiler option
- Zp compiler option
- /Zp compiler option [C++]
- -Zp compiler option [C++]
ms.assetid: 5242f656-ed9b-48a3-bc73-cfcf3ed2520f
ms.openlocfilehash: d1821d8dc5eab202a918893a1e7895151629b551
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53627530"
---
# <a name="zp-struct-member-alignment"></a>/Zp (Wyrównanie członka struktury)

Określa, jak elementy członkowskie struktury są pakowane w pamięci, a następnie określa ten sam pakowania dla wszystkich elementów w module.

## <a name="syntax"></a>Składnia

> **/ ZP**[**1**|**2**|**4**|**8** | **16**]

## <a name="remarks"></a>Uwagi

Po określeniu **/ZP**_n_ opcji, każdy element członkowski struktury po pierwszym jest przechowywany na rozmiarze typ elementu członkowskiego lub *n*-bajtowych granicach (gdzie *n* to 1, 2, 4, 8 lub 16), która kwota jest mniejsza.

Wartości pakowania dostępne są opisane w poniższej tabeli:

|Argument/ZP|Efekt|
|-|-|
|1|Struktury pakietów przy 1-bajtowych granicach. Taki sam jak **/ZP**.|
|2|Struktury pakietów przy 2-bajtowych granicach.|
|4|Struktury pakietów przy 4-bajtowych granicach.|
|8|Struktury pakietów przy 8-bajtowych granicach (domyślnie).|
|16| Struktury pakietów przy 16-bajtowych granicach.|

Nie należy używać tej opcji, chyba że masz wymagania wyraźnego związku.

> [!WARNING]
> Przyjęto założenie, nagłówki C++ w zestawie Windows SDK **/zp8** pakowania. Jeśli może spowodować uszkodzenie pamięci **/ZP** ustawienie to ulegnie zmianie, gdy przy użyciu nagłówków zestawu Windows SDK.

Można również użyć [pakiet](../../preprocessor/pack.md) do sterowania struktury pakowania. Aby uzyskać więcej informacji na temat wyrównania zobacz:

- [align](../../cpp/align-cpp.md)

- [Operator __alignof](../../cpp/alignof-operator.md)

- [__unaligned](../../cpp/unaligned.md)

- [Przykłady wyrównania struktury](../../build/x64-software-conventions.md#examples-of-structure-alignment) — x64 określonych 64

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **C/C++** > **generowania kodu** stronę właściwości.

1. Modyfikowanie **wyrównanie członka struktury** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StructMemberAlignment%2A>.

## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora](../../build/reference/compiler-options.md)
- [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)
