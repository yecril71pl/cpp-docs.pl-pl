---
title: -IMPLIB (Nazwij bibliotekę importowaną) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /implib
- VC.Project.VCLinkerTool.ImportLIbrary
dev_langs:
- C++
helpviewer_keywords:
- IMPLIB linker option
- /IMPLIB linker option
- -IMPLIB linker option
- import libraries, overriding default name
ms.assetid: fe8f71ab-7055-41b5-8ef8-2b97cfa4a432
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 25d997bf7df96d3f6ee518a8b7ca0568a44efa93
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707645"
---
# <a name="implib-name-import-library"></a>/IMPLIB (Nazwij bibliotekę importowaną)

> / IMPLIB:*nazwy pliku*

## <a name="parameters"></a>Parametry

*Nazwa pliku*<br/>
Określone przez użytkownika nazwę biblioteki importu. Zastępuje ona nazwę domyślną.

## <a name="remarks"></a>Uwagi

Opcja /IMPLIB przesłania domyślną nazwę biblioteki importu, która tworzy łącze, podczas tworzenia programu, który zawiera eksporty. Domyślną nazwą jest tworzony na podstawie podstawowej nazwy pliku wyjściowego głównego i rozszerzenia. lib. Program zawiera eksporty, jeśli nie określono co najmniej jeden z następujących czynności:

- [__Declspec(dllexport)](../../cpp/dllexport-dllimport.md) — słowo kluczowe w kodzie źródłowym

- [EKSPORTY](../../build/reference/exports.md) instrukcja w pliku .def

- [/EXPORT](../../build/reference/export-exports-a-function.md) specyfikacji za pomocą polecenia łącza

LINK ignoruje /IMPLIB, gdy nie jest tworzona bibliotekę importu. Jeśli nie określono eksportuje żadnych danych, łącze nie tworzy bibliotekę importu. Jeśli plik eksportu jest używany w kompilacji, łącze przyjęto założenie, że biblioteka importowana już istnieje i nie tworzy jeden. Aby uzyskać informacji na temat bibliotekami importowanymi oraz plikami eksportowanymi, zobacz [odwołanie do biblioteki LIB](../../build/reference/lib-reference.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **zaawansowane** stronę właściwości.

1. Modyfikowanie **bibliotekę importowaną** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ImportLibrary%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)