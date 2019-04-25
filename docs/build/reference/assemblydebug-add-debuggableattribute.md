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
ms.openlocfilehash: b9899ea76b7a23a0d09442fca01e7d968c5e8aa6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273095"
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

Należy jawnie określić, że obrazu zarządzanego były debugowalne. Za pomocą [/zi](z7-zi-zi-debug-information-format.md) samodzielnie nie jest wystarczająca.

Są także inne opcje konsolidatora, które mają wpływ na Generowanie zestawu:

- [/ ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)

- [/ DELAYSIGN](delaysign-partially-sign-an-assembly.md)

- [/ KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)

- [/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/ NOASSEMBLY](noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **debugowania** stronę właściwości.

1. Modyfikowanie **zestaw do debugowania** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AssemblyDebug%2A>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
