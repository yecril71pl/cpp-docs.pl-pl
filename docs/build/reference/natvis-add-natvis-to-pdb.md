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
ms.openlocfilehash: 983cbe4c4bd4164d81b83a23fe19569318d5193c
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424980"
---
# <a name="natvis-add-natvis-to-pdb"></a>/ NATVIS (Dodaj Natvis do PDB)

> / NATVIS:*nazwy pliku*

## <a name="parameters"></a>Parametry

*Nazwa pliku*<br/>
Plik Natvis do dodania do pliku PDB. Ona osadzona wizualizacji debugera w pliku Natvis do PDB.

## <a name="remarks"></a>Uwagi

Opcja /NATVIS osadza wizualizacji debugera, zdefiniowane w pliku Natvis *filename* w pliku PDB, wygenerowanego przez łącze. Dzięki temu debugera wyświetlić wizualizacje, niezależnie od pliku .natvis. Wiele opcji /NATVIS umożliwia osadzanie plików Natvis w wygenerowanym pliku PDB.

LINK ignoruje /NATVIS, gdy plik PDB nie została utworzona przy użyciu [/DEBUG](../../build/reference/debug-generate-debug-info.md) opcji. Aby uzyskać informacji na temat tworzenia i używania pliku .natvis, zobacz [Tworzenie niestandardowych widoków obiektów macierzystych w debugerze programu Visual Studio](/visualstudio/debugger/create-custom-views-of-native-objects).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Wybierz **wiersza polecenia** — strona właściwości w **konsolidatora** folderu.

1. Dodaj opcję /NATVIS **dodatkowe opcje** pola tekstowego.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Ta opcja nie ma programowy odpowiednik.

## <a name="see-also"></a>Zobacz także

[Tworzenie niestandardowych widoków obiektów macierzystych w debugerze programu Visual Studio](/visualstudio/debugger/create-custom-views-of-native-objects)<br/>
[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)
