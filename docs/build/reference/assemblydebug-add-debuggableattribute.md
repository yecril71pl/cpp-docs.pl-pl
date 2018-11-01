---
title: /ASSEMBLYDEBUG (Dodaj DebuggableAttribute)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.AssemblyDebug
- /ASSEMBLYDEBUG
helpviewer_keywords:
- /ASSEMBLYDEBUG linker option
- -ASSEMBLYDEBUG linker option
- ASSEMBLYDEBUG linker option
ms.assetid: 94443af3-470c-41d7-83a0-7434563d7982
ms.openlocfilehash: e9b39791e6537976be37b942292e1b1d42d5f700
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478653"
---
# <a name="assemblydebug-add-debuggableattribute"></a>/ASSEMBLYDEBUG (Dodaj DebuggableAttribute)

```
/ASSEMBLYDEBUG[:DISABLE]
```

/ ASSEMBLYDEBUG emituje **DebuggableAttribute** atrybutu z debugowania informacji śledzenia i wyłącza optymalizacje JIT. To jest taka sama jak określanie następujący atrybut w źródle:

```
[assembly:Debuggable(true, true)];   // same as /ASSEMBLYDEBUG
```

Emituje /ASSEMBLYDEBUG:disable **DebuggableAttribute** atrybut ale wyłącza śledzenie informacji o debugowaniu i włącza optymalizacje JIT. To jest taka sama jak określanie następujący atrybut w źródle:

```
[assembly:Debuggable(false, false)];   // same as /ASSEMBLYDEBUG:DISABLE
```

Wartość domyślna to się nie Emituj **DebuggableAttribute** atrybutu.

DebuggableAttribute mogą być również dodawane do zestawu bezpośrednio w kodzie źródłowym. Na przykład

```
[assembly:Debuggable(true, true)];   // same as /ASSEMBLYDEBUG
```

## <a name="remarks"></a>Uwagi

Należy jawnie określić, że obrazu zarządzanego były debugowalne. Za pomocą [/zi](../../build/reference/z7-zi-zi-debug-information-format.md) samodzielnie nie jest wystarczająca.

Są także inne opcje konsolidatora, które mają wpływ na Generowanie zestawu:

- [/ ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)

- [/ DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)

- [/ KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)

- [/ KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/ NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **debugowania** stronę właściwości.

1. Modyfikowanie **zestaw do debugowania** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AssemblyDebug%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)