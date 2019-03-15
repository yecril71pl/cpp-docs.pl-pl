---
title: /MANIFEST (Tworzenie manifestu dla aplikacji wykonywanych jednocześnie)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.GenerateManifest
helpviewer_keywords:
- -MANIFEST linker option
- /MANIFEST linker option
- MANIFEST linker option
ms.assetid: 98c52e1e-712c-4f49-b149-4d0a3501b600
ms.openlocfilehash: 9a3ca3980a9cdff4e67885b2ad47ffa2385b0774
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807822"
---
# <a name="manifest-create-side-by-side-assembly-manifest"></a>/MANIFEST (Tworzenie manifestu dla aplikacji wykonywanych jednocześnie)

```
/MANIFEST[:{EMBED[,ID=#]|NO}]
```

## <a name="remarks"></a>Uwagi

/ MANIFEST Określa, że konsolidator powinien utworzyć plik manifestu side-by-side. Aby uzyskać więcej informacji na temat plików manifestu, zobacz [odwołania plików manifestu](/windows/desktop/SbsCs/manifest-files-reference).

Wartość domyślna to /MANIFEST.

/MANIFEST: OSADZANIE opcja określa konsolidator należy osadzić pliku manifestu na obrazie, jako zasobu typu RT_MANIFEST. Opcjonalny `ID` parametr jest identyfikator zasobu do użycia dla manifestu. Użyj wartości 1 dla pliku wykonywalnego. Umożliwiają wartość 2 dla bibliotek DLL z nim do określania prywatnych zależności. Jeśli `ID` parametr nie jest określony, wartość domyślna to 2, jeśli ustawiono opcję/dll; w przeciwnym razie wartość domyślna to 1.

Począwszy od programu Visual Studio 2008 plików manifestu dla plików wykonywalnych zawiera sekcja, która określa informacje kontroli konta użytkownika (UAC). Jeśli określono /MANIFEST, ale nie określono [/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md) ani [/dll](dll-build-a-dll.md), fragment funkcji Kontrola konta użytkownika domyślnego, który ma ustawiony poziom kontroli konta użytkownika do *asInvoker* zostaną wstawione do manifestu. Aby uzyskać więcej informacji na temat poziomów funkcji Kontrola konta użytkownika, zobacz [/MANIFESTUAC (osadza informacje UAC w manifeście)](manifestuac-embeds-uac-information-in-manifest.md).

Aby zmienić domyślne zachowanie dla funkcji Kontrola konta użytkownika, wykonaj jeden z nich:

- Wybierz opcję /MANIFESTUAC, a także Ustaw poziom funkcji Kontrola konta użytkownika na żądaną wartość.

- Lub wybierz opcję: No, jeśli nie chcesz wygenerować fragmentu UAC w manifeście.

Jeśli nie określono /MANIFEST, ale określono [/MANIFESTDEPENDENCY](manifestdependency-specify-manifest-dependencies.md) komentarze, tworzony jest plik manifestu. Nie jest tworzony plik manifestu, jeśli określisz /MANIFEST:NO.

Jeśli określisz /MANIFEST, nazwa pliku manifestu jest taka sama jak nazwa pliku wyjściowego, ale manifest dodanym na końcu nazwy pliku. Na przykład jeśli nazwa pliku wyjściowego jest MyFile.exe, nazwa pliku manifestu jest MyFile.exe.manifest.  Jeśli określisz /MANIFESTFILE:*nazwa*, nazwa manifestu to określić w *nazwa*.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Rozwiń **właściwości konfiguracji** węzła.

1. Rozwiń **konsolidatora** węzła.

1. Wybierz **pliku manifestu** stronę właściwości.

1. Modyfikowanie **Generuj Manifest** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateManifest%2A>.

## <a name="see-also"></a>Zobacz także

[Odwołania konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
