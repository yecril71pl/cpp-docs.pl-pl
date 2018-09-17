---
title: -LN (Utwórz moduł MSIL) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /LN
dev_langs:
- C++
helpviewer_keywords:
- -LN compiler option [C++]
- /LN compiler option [C++]
ms.assetid: 4f38f4f4-3176-4caf-8200-5c7585dc1ed3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 74c9ad6d8af797edb25a994f16334d40a3cbf910
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710856"
---
# <a name="ln-create-msil-module"></a>/LN (Utwórz moduł MSIL)

Określa, że nie można wstawić w manifeście zestawu do pliku wyjściowego.

## <a name="syntax"></a>Składnia

```
/LN
```

## <a name="remarks"></a>Uwagi

Domyślnie **/LN** nie jest włączone (manifest zestawu jest wstawiany do pliku wyjściowego).

Gdy **/LN** jest używany, jeden z [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md) opcje musi też być używane.

Zarządzany program, który nie ma metadane zestawu w manifeście nosi nazwę modułu. Jeśli kompilujesz z opcją [/c (Kompiluj bez konsolidacji)](../../build/reference/c-compile-without-linking.md) i **/LN**, określ [/noassembly (Utwórz moduł MSIL)](../../build/reference/noassembly-create-a-msil-module.md) w fazie konsolidator, aby utworzyć plik wyjściowy.

Można utworzyć modułów, jeśli chcesz wykonać to oparty na komponentach podejście do tworzenia zestawów.  Oznacza to, że możesz tworzyć typy i kompilowania ich do modułów.  Następnie można wygenerować zestawu z jednego lub więcej modułów.  Aby uzyskać więcej informacji na temat tworzenia zestawów z modułów, zobacz [pliki .netmodule — wejście konsolidatora](../../build/reference/netmodule-files-as-linker-input.md) lub [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).

Domyślnym rozszerzeniem pliku modułu jest .netmodule.

W wersjach Visual C++ przed Visual C++ 2005, moduł został utworzony za pomocą **/clr:noAssembly**.

Konsolidator Visual C++ akceptuje pliki .netmodule — wejście plik wyjściowy, generowany przez konsolidator. zostanie ona zestaw lub moduł .netmodule z ma zależności środowiska wykonawczego na żadnym z modułów .netmodule, że dane wejściowe do konsolidatora.  Aby uzyskać więcej informacji, zobacz [pliki .netmodule — wejście konsolidatora](../../build/reference/netmodule-files-as-linker-input.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

- Określ [/noassembly (Utwórz moduł MSIL)](../../build/reference/noassembly-create-a-msil-module.md) w fazie konsolidator, aby utworzyć plik wyjściowy.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Nie można programowo zmienić tę opcję kompilatora.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)