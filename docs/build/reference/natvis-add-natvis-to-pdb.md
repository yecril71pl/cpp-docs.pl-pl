---
title: / NATVIS (Dodaj Natvis do PDB)
ms.date: 08/10/2017
f1_keywords:
- /natvis
- VC.Project.VCLinkerTool.ImportLIbrary
helpviewer_keywords:
- NATVIS linker option
- /NATVIS linker option
- -NATVIS linker option
- Add Natvis file to PDB
ms.assetid: 8747fc0c-701a-4796-bb4d-818ab4465cca
ms.openlocfilehash: e758a49b41a17d805b752947cd1944087c8ff852
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809239"
---
# <a name="natvis-add-natvis-to-pdb"></a>/ NATVIS (Dodaj Natvis do PDB)

> / NATVIS:*nazwy pliku*

## <a name="parameters"></a>Parametry

*Nazwa pliku*<br/>
Plik Natvis do dodania do pliku PDB. Ona osadzona wizualizacji debugera w pliku Natvis do PDB.

## <a name="remarks"></a>Uwagi

Opcja /NATVIS osadza wizualizacji debugera, zdefiniowane w pliku Natvis *filename* w pliku PDB, wygenerowanego przez łącze. Dzięki temu debugera wyświetlić wizualizacje, niezależnie od pliku .natvis. Wiele opcji /NATVIS umożliwia osadzanie plików Natvis w wygenerowanym pliku PDB.

LINK ignoruje /NATVIS, gdy plik PDB nie została utworzona przy użyciu [/DEBUG](debug-generate-debug-info.md) opcji. Aby uzyskać informacji na temat tworzenia i używania pliku .natvis, zobacz [Tworzenie niestandardowych widoków obiektów macierzystych w debugerze programu Visual Studio](/visualstudio/debugger/create-custom-views-of-native-objects).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **wiersza polecenia** — strona właściwości w **konsolidatora** folderu.

1. Dodaj opcję /NATVIS **dodatkowe opcje** pola tekstowego.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Ta opcja nie ma programowy odpowiednik.

## <a name="see-also"></a>Zobacz także

[Odwołania konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
