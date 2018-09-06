---
title: Kompilowanie biblioteki importowanej oraz pliku eksportowanego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-tools
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c832ee24d500eba28c14713d1c0a092baf90a440
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894619"
---
# <a name="building-an-import-library-and-export-file"></a>Kompilowanie biblioteki importowanej oraz pliku eksportowanego

Do tworzenia biblioteki importu i eksportu plików, użyj następującej składni:

> **/ DEF LIB**[**:**<em>deffile</em>] [*opcje*] [*objfiles*] [*bibliotek*]

Jeśli określono/DEF, pliki wyjściowe LIB tworzy na podstawie specyfikacje eksportu, które są przekazywane w poleceniu LIB. Istnieją trzy metody Określanie eksportów, wymienione w zalecanej kolejności używania:

1. A **__declspec(dllexport)** definicji w jednym z *objfiles* lub *biblioteki*

2. Specyfikacji/Export:*nazwa* w wierszu polecenia LIB

3. Definicja w **EKSPORTÓW** instrukcji w *deffile*

Są to te same metody, które służy do określania eksporty podczas łączenia z eksportu programu. Program można używać więcej niż jednej metody. Można określić część polecenia LIB (takich jak wiele *objfiles* lub specyfikacji/Export) w pliku poleceń w poleceniu LIB, podobnie jak wykonywać następujące czynności za pomocą polecenia łącza.

Następujące opcje dotyczą kompilowania biblioteki importowanej i eksportowanie pliku:

> **/ OUT:** *importowania*  

Przesłania domyślną nazwę pliku wyjściowego dla *zaimportować* biblioteki tworzona. Gdy out nie zostanie określony, domyślną nazwą jest podstawowa nazwa pierwszego pliku obiektu lub biblioteki w poleceniu LIB i rozszerzenia. lib. Plik eksportu otrzymuje taką samą nazwę jak biblioteki importowanej oraz rozszerzenie. oczekiwane.

> **/ EXPORT:** *Nazwa_wpisu* \[ **=** *internalname*]\[,**\@** <em>porządkowe</em>\[, **NONAME**]]\[, **danych**]

Eksportuje funkcję z programu, aby zezwolić na inne programy w wywołaniu funkcji. Można także eksportować dane (przy użyciu **danych** — słowo kluczowe). Eksporty są zazwyczaj zdefiniowane w bibliotece DLL.

*Nazwa_wpisu* jest nazwa elementu funkcję lub dane, ponieważ jest używane przez program wywołujący. Opcjonalnie można określić *internalname* jako funkcja znane w programie definiujące; domyślnie *internalname* jest taka sama jak *Nazwa_wpisu*. *Porządkowe* Określa indeks w tabeli eksportu do zakresu od 1 do 65 535; Jeśli nie określisz *porządkowe*, LIB przypisuje jeden. **NONAME** — słowo kluczowe eksportuje funkcję tylko jako liczby porządkowej, bez *Nazwa_wpisu*. **Danych** — słowo kluczowe jest używany do eksportowania obiektów tylko do danych.

> **/ INCLUDE:** *symboli*

Dodaje określony *symbol* do tabeli symboli. Ta opcja jest przydatne w przypadku wymuszania użycie obiektu biblioteki, które w przeciwnym razie nie będzie uwzględniony.

Należy pamiętać, że jeśli tworzysz biblioteki importu w krok wstępny, przed utworzeniem usługi .dll, należy przekazać ten sam zestaw plików obiektów podczas tworzenia pliku .dll, jako zakończony powodzeniem w podczas kompilowania biblioteki importowanej.

## <a name="see-also"></a>Zobacz też

[Praca z bibliotekami importowanymi oraz plikami eksportowanymi](../../build/reference/working-with-import-libraries-and-export-files.md)