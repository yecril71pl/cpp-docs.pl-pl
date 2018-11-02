---
title: /VERSION (Informacje o wersji)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.Version
- /version
helpviewer_keywords:
- -VERSION linker option
- Version Information linker option
- version numbers, specifying in .exe
- /VERSION linker option
- VERSION linker option
ms.assetid: b86d0e86-dca6-4316-aee2-d863ccb9f223
ms.openlocfilehash: 3e24a5307b8c4f60f29de390d38d9694f1cacf29
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50529704"
---
# <a name="version-version-information"></a>/VERSION (Informacje o wersji)

```
/VERSION:major[.minor]
```

## <a name="arguments"></a>Argumenty

*główne* i *pomocnicza*<br/>
Numer wersji, które mają w nagłówku pliku .exe lub .dll.

## <a name="remarks"></a>Uwagi

Opcja / Version informuje konsolidator, aby umieścił numer wersji w nagłówku pliku .exe lub .dll. Użyj polecenia DUMPBIN [/HEADERS](../../build/reference/headers.md) aby zobaczyć pole wersji obrazu OPCJONALNYCH wartości NAGŁÓWKA, aby zobaczyć efekt Version.

*Głównych* i *pomocnicza* argumenty są liczbami dziesiętnymi z zakresu od 0 do 65 535. Wartość domyślna to wersja 0,0.

Informacje o określony za pomocą Version nie ma wpływu na informacje o wersji, który pojawia się dla aplikacji, gdy wyświetlić jego właściwości w Eksploratorze plików. Czy informacje o wersji pochodzą z pliku zasobu, który jest używany do tworzenia aplikacji. Zobacz [Edytor informacji o wersji](../../windows/version-information-editor.md) Aby uzyskać więcej informacji.

Innym sposobem, aby wstawić numer wersji jest [wersji](../../build/reference/version-c-cpp.md) instrukcji definicji modułu.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **ogólne** stronę właściwości.

1. Modyfikowanie **wersji** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Version%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)