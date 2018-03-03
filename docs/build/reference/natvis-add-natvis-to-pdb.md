---
title: -NATVIS (Dodaj Natvis do PDB) | Dokumentacja firmy Microsoft
ms.date: 08/10/2017
ms.tgt_pltfrm: 
ms.technology:
- cpp-tools
ms.topic: article
f1_keywords:
- /natvis
- VC.Project.VCLinkerTool.ImportLIbrary
dev_langs:
- C++
helpviewer_keywords:
- NATVIS linker option
- /NATVIS linker option
- -NATVIS linker option
- Add Natvis file to PDB
ms.assetid: 8747fc0c-701a-4796-bb4d-818ab4465cca
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 20715b48413a705aa2338e7e37538171e4141cad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="natvis-add-natvis-to-pdb"></a>/ NATVIS (Dodaj Natvis do PDB)
  
> / NATVIS:*filename*  
  
## <a name="parameters"></a>Parametry  
  
*Nazwa pliku*  
Plik Natvis do dodania do pliku PDB. Ją osadza wizualizacje debugera w pliku Natvis w pliku PDB.  
  
## <a name="remarks"></a>Uwagi  
  
Opcja /NATVIS osadza wizualizacje debugera zdefiniowane w pliku Natvis *filename* w pliku PDB wygenerowany przez łącze. Dzięki temu debugera wyświetlić wizualizacji niezależnie od pliku .natvis. Wiele opcji /NATVIS służy do osadzenia w wygenerowanym pliku PDB więcej niż jeden plik Natvis.  
  
W przypadku pliku PDB nie jest tworzona przy użyciu łącza ignoruje /NATVIS [/DEBUG](../../build/reference/debug-generate-debug-info.md) opcji. Informacje dotyczące tworzenia i korzystania z plików .natvis, zobacz [Tworzenie niestandardowych widoków obiektów macierzystych w debugerze programu Visual Studio](/visualstudio/debugger/create-custom-views-of-native-objects).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **wiersza polecenia** stronę właściwości w **konsolidatora** folderu.  
  
3.  Dodaj opcję /NATVIS **dodatkowe opcje** pola tekstowego.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Ta opcja nie ma odpowiednika programowe.  
  
## <a name="see-also"></a>Zobacz też  
  
[Tworzenie niestandardowych widoków obiektów macierzystych w debugerze programu Visual Studio](/visualstudio/debugger/create-custom-views-of-native-objects)  
[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)  
[Opcje konsolidatora](../../build/reference/linker-options.md)