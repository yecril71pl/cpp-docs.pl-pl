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
ms.openlocfilehash: d963a7145ab2e8c8872dc21c485bdc8f877b0b76
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493142"
---
# <a name="allowbind-prevent-dll-binding"></a>/ALLOWBIND (Zapobiegaj powiązaniu biblioteki DLL)

```
/ALLOWBIND[:NO]
```

## <a name="remarks"></a>Uwagi

/ALLOWBIND: NO ustawia bit w nagłówku DLL, który wskazuje na powiązanie. exe, że obraz nie może być powiązany. Nie ma potrzeby powiązania DLL, jeśli został podpisany cyfrowo (powiązanie unieważnia sygnaturę).

Istniejącą bibliotekę DLL dla funkcji/ALLOWBIND można edytować za pomocą opcji [/ALLOWBIND](allowbind.md) narzędzia polecenia EDITBIN.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Rozwiń węzeł **Właściwości konfiguracji**, **konsolidator**, a następnie wybierz pozycję **wiersz polecenia**.

1. Wprowadź `/ALLOWBIND:NO` **dodatkowe opcje**.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)<br/>
[BindImage, funkcja](/windows/win32/api/imagehlp/nf-imagehlp-bindimage)<br/>
[BindImageEx, funkcja](/windows/win32/api/imagehlp/nf-imagehlp-bindimageex)
