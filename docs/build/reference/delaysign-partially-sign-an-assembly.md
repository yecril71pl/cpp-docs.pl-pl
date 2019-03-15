---
title: /DELAYSIGN (Częściowo podpisz zestaw)
ms.date: 11/04/2016
f1_keywords:
- /delaysign
- VC.Project.VCLinkerTool.DelaySign
helpviewer_keywords:
- /DELAYSIGN linker option
- DELAYSIGN linker option
- -DELAYSIGN linker option
ms.assetid: 15244d30-3ecb-492f-a408-ffe81f38de20
ms.openlocfilehash: 65585b856627ad9fda5a8f8bfad6ad81fef0f81c
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807653"
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

**/DelaySign** opcja nie ma wpływu, chyba że używana z [/KeyFile](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) lub [/KeyContainer](keycontainer-specify-a-key-container-to-sign-an-assembly.md).

W przypadku żądania całkowicie podpisanego zestawu, kompilator tworzy skrót pliku który zawiera manifest (metadane zestawu) i podpisuje skrót przy użyciu klucza prywatnego. Wynikowy podpis cyfrowy jest przechowywany w pliku, który zawiera manifest. Gdy zestaw jest podpisany z opóźnieniem, konsolidator nie obliczeniowe i przechowuj podpisu, ale rezerwuje miejsce w pliku, aby podpis mógł zostać dodany później.

Na przykład za pomocą **/DelaySign** umożliwia testerowi umieszczenie zestawu w globalnej pamięci podręcznej. Po zakończeniu testowania można całkowicie podpisać zestaw, umieszczając klucza prywatnego w zestawie.

Zobacz [zestawy o silnej nazwach (podpisywanie zestawów) (C + +/ CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md) i [opóźnienie podpisywania zestawu](/dotnet/framework/app-domains/delay-sign-assembly) więcej informacji na temat podpisywania zestawu.

Są także inne opcje konsolidatora, które mają wpływ na Generowanie zestawu:

- [/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)

- [/ ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)

- [/ NOASSEMBLY](noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje w **dodatkowe opcje** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Odwołania konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
