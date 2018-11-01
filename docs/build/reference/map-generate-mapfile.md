---
title: /MAP (Generuj plik mapy)
ms.date: 11/04/2016
f1_keywords:
- /map
- VC.Project.VCLinkerTool.MapFileName
- VC.Project.VCLinkerTool.GenerateMapFile
helpviewer_keywords:
- mapfiles, creating linker
- generate mapfile linker option
- mapfile linker option
- mapfiles, information about program being linked
- MAP linker option
- -MAP linker option
- mapfiles, specifying file name
- /MAP linker option
ms.assetid: 9ccce53d-4e36-43da-87b0-7603ddfdea63
ms.openlocfilehash: 8ff2a8f54caa54247050c607004ed328c0d1b11d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436457"
---
# <a name="map-generate-mapfile"></a>/MAP (Generuj plik mapy)

```
/MAP[:filename]
```

## <a name="arguments"></a>Argumenty

*Nazwa pliku*<br/>
Określone przez użytkownika nazwa pliku mapfile. Zastępuje ona nazwę domyślną.

## <a name="remarks"></a>Uwagi

Opcja/map informuje konsolidator, aby utworzył plik mapowania.

Domyślnie konsolidator nazwy pliku mapfile z podstawowej nazwy programu i map rozszerzenia. Opcjonalny *filename* służy do przesłaniania domyślnej nazwy dla pliku mapowania.

Plik mapy jest plik tekstowy, który zawiera następujące informacje o podłączanym programie:

- Nazwa modułu, który jest nazwa podstawowa pliku

- Sygnaturę czasową od nagłówka pliku programu, (a nie z systemu plików)

- Lista grup w programie, przy użyciu adresu początkowego każdej grupy (jako *sekcji*:*przesunięcie*), długość, nazwę grupy i klasy

- Lista symboli publicznych, przy użyciu poszczególnych adresów (jako *sekcji*:*przesunięcie*), symbolu nazwę, adres płaskie i pliku .obj, na którym jest zdefiniowany symbol

- Punkt wejścia (jako *sekcji*:*przesunięcie*)

[/MapInfo](../../build/reference/mapinfo-include-information-in-mapfile.md) opcja określa dodatkowe informacje, które mają zostać uwzględnione w pliku mapfile.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **debugowania** stronę właściwości.

1. Modyfikowanie **Generuj plik mapy** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateMapFile%2A> i <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MapFileName%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)