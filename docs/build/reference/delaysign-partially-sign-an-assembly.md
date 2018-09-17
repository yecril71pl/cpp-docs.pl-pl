---
title: -DELAYSIGN (częściowo Podpisz zestaw) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /delaysign
- VC.Project.VCLinkerTool.DelaySign
dev_langs:
- C++
helpviewer_keywords:
- /DELAYSIGN linker option
- DELAYSIGN linker option
- -DELAYSIGN linker option
ms.assetid: 15244d30-3ecb-492f-a408-ffe81f38de20
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f1551789c800e298396d932a4cc8c4f65aa6c79
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45699806"
---
# <a name="delaysign-partially-sign-an-assembly"></a>/DELAYSIGN (Częściowo podpisz zestaw)

```
/DELAYSIGN[:NO]
```

## <a name="arguments"></a>Argumenty

**BRAK**<br/>
Określa, czy zestaw powinien być częściowo niepodpisana.

## <a name="remarks"></a>Uwagi

Użyj **/DelaySign** Jeśli chcesz tylko umieścić klucz publiczny w zestawie. Wartość domyślna to **/DelaySign: No**.

**/DelaySign** opcja nie ma wpływu, chyba że używana z [/KeyFile](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) lub [/KeyContainer](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md).

W przypadku żądania całkowicie podpisanego zestawu, kompilator tworzy skrót pliku który zawiera manifest (metadane zestawu) i podpisuje skrót przy użyciu klucza prywatnego. Wynikowy podpis cyfrowy jest przechowywany w pliku, który zawiera manifest. Gdy zestaw jest podpisany z opóźnieniem, konsolidator nie obliczeniowe i przechowuj podpisu, ale rezerwuje miejsce w pliku, aby podpis mógł zostać dodany później.

Na przykład za pomocą **/DelaySign** umożliwia testerowi umieszczenie zestawu w globalnej pamięci podręcznej. Po zakończeniu testowania można całkowicie podpisać zestaw, umieszczając klucza prywatnego w zestawie.

Zobacz [zestawy o silnej nazwach (podpisywanie zestawów) (C + +/ CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md) i [opóźnienie podpisywania zestawu](/dotnet/framework/app-domains/delay-sign-assembly) więcej informacji na temat podpisywania zestawu.

Są także inne opcje konsolidatora, które mają wpływ na Generowanie zestawu:

- [/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)

- [/ ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)

- [/ NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje w **dodatkowe opcje** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)