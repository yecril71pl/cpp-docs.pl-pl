---
title: /IMPLIB (Nazwij bibliotekę importowaną)
ms.date: 11/04/2016
f1_keywords:
- /implib
- VC.Project.VCLinkerTool.ImportLIbrary
helpviewer_keywords:
- IMPLIB linker option
- /IMPLIB linker option
- -IMPLIB linker option
- import libraries, overriding default name
ms.assetid: fe8f71ab-7055-41b5-8ef8-2b97cfa4a432
ms.openlocfilehash: dc9a9220d55f7831a00f70ec155cc5b57a695818
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269989"
---
# <a name="implib-name-import-library"></a>/IMPLIB (Nazwij bibliotekę importowaną)

> / IMPLIB:*nazwy pliku*

## <a name="parameters"></a>Parametry

*Nazwa pliku*<br/>
Określone przez użytkownika nazwę biblioteki importu. Zastępuje ona nazwę domyślną.

## <a name="remarks"></a>Uwagi

Opcja /IMPLIB przesłania domyślną nazwę biblioteki importu, która tworzy łącze, podczas tworzenia programu, który zawiera eksporty. Domyślną nazwą jest tworzony na podstawie podstawowej nazwy pliku wyjściowego głównego i rozszerzenia. lib. Program zawiera eksporty, jeśli nie określono co najmniej jeden z następujących czynności:

- [__Declspec(dllexport)](../../cpp/dllexport-dllimport.md) — słowo kluczowe w kodzie źródłowym

- [EKSPORTY](exports.md) instrukcja w pliku .def

- [/EXPORT](export-exports-a-function.md) specyfikacji za pomocą polecenia łącza

LINK ignoruje /IMPLIB, gdy nie jest tworzona bibliotekę importu. Jeśli nie określono eksportuje żadnych danych, łącze nie tworzy bibliotekę importu. Jeśli plik eksportu jest używany w kompilacji, łącze przyjęto założenie, że biblioteka importowana już istnieje i nie tworzy jeden. Aby uzyskać informacji na temat bibliotekami importowanymi oraz plikami eksportowanymi, zobacz [odwołanie do biblioteki LIB](lib-reference.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **zaawansowane** stronę właściwości.

1. Modyfikowanie **bibliotekę importowaną** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ImportLibrary%2A>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
