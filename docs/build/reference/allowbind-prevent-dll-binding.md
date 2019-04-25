---
title: /ALLOWBIND (Zapobiegaj powiązaniu biblioteki DLL)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.PreventDLLBinding
- /allowbind
helpviewer_keywords:
- /ALLOWBIND linker option
- binding DLLs
- preventing DLL binding
- ALLOWBIND linker option
- -ALLOWBIND linker option
- DLLs [C++], preventing binding
ms.assetid: 30e37e24-12e4-407e-988a-39d357403598
ms.openlocfilehash: bd9976e434441d2480386ee6fa3d0315fd8d2ef5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295154"
---
# <a name="allowbind-prevent-dll-binding"></a>/ALLOWBIND (Zapobiegaj powiązaniu biblioteki DLL)

```
/ALLOWBIND[:NO]
```

## <a name="remarks"></a>Uwagi

/ALLOWBIND:no Ustawia bit w nagłówku biblioteki DLL, która wskazuje Bind.exe, że obraz nie może być powiązana. Nie ma Biblioteka DLL była związana, jeśli jego została podpisana cyfrowo (powiązanie unieważnia podpis).

Można edytować istniejącej biblioteki DLL dla funkcjonalność /ALLOWBIND [/ALLOWBIND](allowbind.md) — opcja polecenia EDITBIN narzędzia.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Rozwiń **właściwości konfiguracji**, **konsolidatora**i wybierz **wiersza polecenia**.

1. Wprowadź `/ALLOWBIND:NO` do **dodatkowe opcje**.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)<br/>
[BindImage — funkcja](/windows/desktop/api/imagehlp/nf-imagehlp-bindimage)<br/>
[BindImageEx — funkcja](/windows/desktop/api/imagehlp/nf-imagehlp-bindimageex)
