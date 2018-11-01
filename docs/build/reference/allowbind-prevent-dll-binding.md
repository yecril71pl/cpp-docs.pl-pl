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
ms.openlocfilehash: ffe32a1df1fb85c7ae47b07c1ada6c53b269f5f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667301"
---
# <a name="allowbind-prevent-dll-binding"></a>/ALLOWBIND (Zapobiegaj powiązaniu biblioteki DLL)

```
/ALLOWBIND[:NO]
```

## <a name="remarks"></a>Uwagi

/ALLOWBIND:no Ustawia bit w nagłówku biblioteki DLL, która wskazuje Bind.exe, że obraz nie może być powiązana. Nie ma Biblioteka DLL była związana, jeśli jego została podpisana cyfrowo (powiązanie unieważnia podpis).

Można edytować istniejącej biblioteki DLL dla funkcjonalność /ALLOWBIND [/ALLOWBIND](../../build/reference/allowbind.md) — opcja polecenia EDITBIN narzędzia.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Rozwiń **właściwości konfiguracji**, **konsolidatora**i wybierz **wiersza polecenia**.

1. Wprowadź `/ALLOWBIND:NO` do **dodatkowe opcje**.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)<br/>
[BindImage — funkcja](/windows/desktop/api/imagehlp/nf-imagehlp-bindimage)<br/>
[BindImageEx — funkcja](/windows/desktop/api/imagehlp/nf-imagehlp-bindimageex)