---
title: Kompilowanie biblioteki importowanej oraz pliku eksportowanego | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLibrarianTool.ModuleDefinitionFile
- VC.Project.VCLibrarianTool.ExportNamedFunctions
- VC.Project.VCLibrarianTool.GenerateDebug
- VC.Project.VCLibrarianTool.ForceSymbolReferences
dev_langs:
- C++
helpviewer_keywords:
- OUT library manager option
- INCLUDE library manager option
- /DEF library manager option
- exporting data
- import libraries, building
- -INCLUDE library manager option
- /OUT library manager option
- DEF library manager option
- -DEF library manager option
- -OUT library manager option
- /INCLUDE library manager option
- -EXPORT library manager option
- exporting data, export (.exp) files
- /EXPORT library manager option
- EXPORT library manager option
- .lib files
- EXP files
ms.assetid: 2fe4f30a-1dd6-4b05-84b5-0752e1dee354
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 979e052147f058e6c46a1c10b1dd89cfd36ee362
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="building-an-import-library-and-export-file"></a>Kompilowanie biblioteki importowanej oraz pliku eksportowanego
Do tworzenia biblioteki importu i eksportu pliku, użyj następującej składni:  
  
```  
LIB /DEF[:deffile] [options] [objfiles] [libraries]  
```  
  
 Jeśli określono opcję/DEF, pliki wyjściowe LIB tworzy na podstawie specyfikacje eksportu, które są przekazywane do polecenia LIB. Istnieją trzy metody Określanie eksportów wymienione w kolejności zalecane użycie:  
  
1.  A **__declspec(dllexport)** definicji w jednym z *objfiles* lub *biblioteki*  
  
2.  Specyfikacji/Export:*nazwa* w wierszu polecenia LIB  
  
3.  Definicja w **EKSPORTÓW** instrukcji w`deffile`  
  
 Są to te same metody używanej do określenia eksportu podczas łączenia programu eksportowanie. Program można używać więcej niż jedna metoda. Można określić części polecenia LIB (takich jak wiele *objfiles* lub specyfikacji/Export) w pliku poleceń w poleceniu LIB, podobnie jak można w poleceniu łącza.  
  
 Następujące opcje dotyczą kompilowania biblioteki importowanej i wyeksportuj plik:  
  
 / OUT: *importowania*  
 Przesłania domyślną nazwę pliku wyjściowego dla *zaimportować* biblioteki tworzona. Jeśli nie określono/out, domyślna nazwa jest nazwą podstawowej pierwszego obiektu pliku lub biblioteki w poleceniu LIB i rozszerzenia. lib. Wyeksportowany plik znajduje się taką samą nazwę podstawową jak biblioteki importowanej oraz rozszerzenia. exp.  
  
 / EXPORT: *Nazwa_wpisu*[= *internalname*] [, @ `ordinal`[, **NONAME**]] [, **danych**]  
 Eksportuje funkcję z programu zezwala na wywołanie funkcji innych programów. Można również eksportować dane (przy użyciu **danych** — słowo kluczowe). Eksporty są zazwyczaj definiowane w bibliotece DLL.  
  
 *Nazwa_wpisu* jest nazwa elementu funkcję lub dane, ponieważ jest używane przez program wywołujący. Opcjonalnie można określić *internalname* jako funkcja znane w programie definiującego; domyślnie *internalname* jest taka sama jak *Nazwa_wpisu*. `ordinal` Określa indeks do tabeli eksportu w zakresie od 1 do 65 535; Jeśli nie określisz `ordinal`, LIB przypisuje jeden. **NONAME** — słowo kluczowe eksportuje funkcję tylko jako numer bez *Nazwa_wpisu*. **Danych** — słowo kluczowe jest używany do eksportowania obiektów tylko do danych.  
  
 / INCLUDE:`symbol`  
 Dodaje określony symbol do tabeli symboli. Ta opcja jest przydatna do wymuszania użycia obiektu biblioteki, które w przeciwnym razie nie będą uwzględniane.  
  
 Należy pamiętać, że w przypadku utworzenia biblioteki importu w krok wstępny, przed utworzeniem sieci dll, należy podać ten sam zestaw plików obiektów podczas tworzenia biblioteki dll, jako przekazaną podczas tworzenia biblioteki importu.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z bibliotekami importowanymi oraz plikami eksportowanymi](../../build/reference/working-with-import-libraries-and-export-files.md)