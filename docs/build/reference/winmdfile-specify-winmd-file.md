---
title: /WINMDFILE (określ plik winmd)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadataFile
ms.assetid: 062b41b3-14d6-432c-a361-fdb66e918931
ms.openlocfilehash: 5d24d1d1aad8442f549dcb1aa4bd6414070c282c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316486"
---
# <a name="winmdfile-specify-winmd-file"></a>/WINMDFILE (określ plik winmd)

Określa nazwę pliku dla pliku wyjściowego metadanych środowiska wykonawczego Windows (winmd), który jest generowany przez [/WINMD](winmd-generate-windows-metadata.md) — opcja konsolidatora.

```
/WINMDFILE:filename
```

## <a name="remarks"></a>Uwagi

Użyj wartości, który jest określony w `filename` do przesłaniania domyślnej nazwy pliku winmd (`binaryname`winmd). Należy zauważyć, że nie dołączaj ".winmd" do `filename`.  Jeśli wiele wartości nie są wyświetlane na **/winmdfile** wiersza polecenia, ostatni z nich ma pierwszeństwo.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **konsolidatora** folderu.

1. Wybierz **metadanych Windows** stronę właściwości.

1. W **plik metadanych Windows** wpisz lokalizację pliku.

## <a name="see-also"></a>Zobacz także

[/WINMD (Generuj metadane systemu Windows)](winmd-generate-windows-metadata.md)<br/>
[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
