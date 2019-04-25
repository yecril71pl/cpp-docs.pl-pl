---
title: /KEYFILE (Określ klucz lub parę kluczy, aby podpisać zestaw)
ms.date: 11/04/2016
f1_keywords:
- /keyfile
- VC.Project.VCLinkerTool.KeyFile
helpviewer_keywords:
- /KEYFILE linker option
- -KEYFILE linker option
- KEYFILE linker option
ms.assetid: 9b71f8c0-541c-4fe5-a0c7-9364f42ecb06
ms.openlocfilehash: d309390c1ac1a19d9d4a982908dbbbac0bd52714
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291564"
---
# <a name="keyfile-specify-key-or-key-pair-to-sign-an-assembly"></a>/KEYFILE (Określ klucz lub parę kluczy, aby podpisać zestaw)

```
/KEYFILE:filename
```

## <a name="arguments"></a>Argumenty

*Nazwa pliku*<br/>
Plik, który zawiera klucz. Umieścić ciąg w podwójnym cudzysłowie ("") zawiera spację.

## <a name="remarks"></a>Uwagi

Konsolidator wstawia klucz publiczny w manifeście zestawu, a następnie podpisuje ostateczny zestaw przy użyciu klucza prywatnego. Aby wygenerować plik klucza, wpisz [sn -k](/dotnet/framework/tools/sn-exe-strong-name-tool) *filename* w wierszu polecenia. Zestawu podpisanego za pomocą jest nazywany ma silnej nazwy.

Jeśli kompilujesz z opcją [/LN](ln-create-msil-module.md), nazwę pliku klucza jest przechowywany w module i włączyć do zestawu, który jest tworzony podczas kompilowania zestawu, który zawiera jawnego odwołania do modułu, za pośrednictwem [#using](../../preprocessor/hash-using-directive-cpp.md), lub podczas łączenia z [assemblymodule](assemblymodule-add-a-msil-module-to-the-assembly.md).

Można również przekazać dane szyfrowania do konsolidatora z [/KeyContainer](keycontainer-specify-a-key-container-to-sign-an-assembly.md). Użyj [/DelaySign](delaysign-partially-sign-an-assembly.md) Jeśli chcesz, aby częściowo podpisany zestawu. Zobacz [zestawy o silnej nazwach (podpisywanie zestawów) (C++sposób niezamierzony)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md) więcej informacji na temat podpisywania zestawu.

W przypadku obu **/KeyFile** i **/KeyContainer** podano (przez opcję wiersza polecenia lub przez atrybut niestandardowy), konsolidator próbują używać najpierw kontenera kluczy. Jeśli się to powiedzie, zestaw zostanie podpisany przy użyciu informacji z kontenera kluczy. Konsolidator nie znajdzie kontenera kluczy, spróbuje pliku określonego przez/KeyFile. Jeśli się to powiedzie, zestaw zostanie podpisany przy użyciu informacji z pliku klucza, a informacje o kluczu zostanie zainstalowany w kontenerze kluczy (podobnie jak sn -i), aby przy następnej kompilacji będzie obowiązywać kontenera kluczy.

Należy pamiętać, że plik klucza może zawierać tylko klucz publiczny.

Zobacz [tworzenie i zestawy Using Strong-Named](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies) więcej informacji na temat podpisywania zestawu.

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

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
