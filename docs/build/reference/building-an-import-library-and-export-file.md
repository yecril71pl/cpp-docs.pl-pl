---
title: Kompilowanie biblioteki importowanej oraz pliku eksportowanego
ms.date: 09/05/2018
f1_keywords:
- VC.Project.VCLibrarianTool.ModuleDefinitionFile
- VC.Project.VCLibrarianTool.ExportNamedFunctions
- VC.Project.VCLibrarianTool.GenerateDebug
- VC.Project.VCLibrarianTool.ForceSymbolReferences
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
ms.openlocfilehash: 5cb5224b3edaf84dbcb7c0429044a647fb5ac19a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229756"
---
# <a name="building-an-import-library-and-export-file"></a>Kompilowanie biblioteki importowanej oraz pliku eksportowanego

Aby utworzyć bibliotekę importu i wyeksportować plik, należy użyć następującej składni:

> **Lib/def**[**:**<em>deffile</em>] [*Opcje*] [*objfiles*] [*biblioteki*]

Gdy/DEF jest określony, LIB tworzy pliki wyjściowe z specyfikacji eksportu, które są przekazywane w LIB polecenie. Istnieją trzy metody określania eksportu, wymienione w zalecanej kolejności użycia:

1. **`__declspec(dllexport)`** Definicja w jednej z *objfiles* lub *bibliotek*

1. Specyfikacja/EXPORT:*name* w wierszu polecenia LIB

1. Definicja w instrukcji **eksports** w *deffile*

Są to te same metody, które służą do określania eksportu podczas łączenia programu eksportu. Program może używać więcej niż jednej metody. Możesz określić części polecenia LIB (takie jak wiele specyfikacji *objfiles* lub/Export) w pliku poleceń w lib polecenia, tak jak w przypadku polecenia link.

Następujące opcje dotyczą tworzenia biblioteki importu i eksportu pliku:

> **/Out:** *Import*

Zastępuje domyślną nazwę pliku wyjściowego dla tworzonej biblioteki *importu* . Gdy nie określono parametru/OUT, domyślną nazwą jest podstawowa nazwa pierwszego pliku obiektu lub biblioteki w poleceniu LIB i Extension. lib. Plik eksportu ma taką samą nazwę podstawową jak biblioteka importowana i rozszerzenie. EXP.

> **/Export:** *EntryName* \[ **=** *InternalName*] \[ , **\@** <em>porządkowy</em> \[ , **NoName**]] \[ , **dane**]

Eksportuje funkcję z programu, aby umożliwić innym programom wywoływanie funkcji. Możesz również eksportować dane (za pomocą słowa kluczowego **danych** ). Eksporty są zwykle zdefiniowane w bibliotece DLL.

*EntryName* jest nazwą funkcji lub elementu danych, która ma być używana przez program wywołujący. Opcjonalnie można określić *wewnętrznyname* jako funkcję znaną w programie definiującym; Domyślnie *wewnętrznaname* jest taka sama jak *EntryName*. *Numer porządkowy* Określa indeks w tabeli eksportu z zakresu od 1 do 65 535; Jeśli nie określisz *liczby porządkowej*, lib przypisuje jeden. Słowo kluczowe **NoName** eksportuje funkcję tylko jako numer porządkowy bez *wpisu*. Słowo kluczowe **Data** służy do eksportowania obiektów tylko do danych.

> **/Include:** *symbol*

Dodaje określony *symbol* do tabeli symboli. Ta opcja jest przydatna do wymuszania użycia obiektu biblioteki, który w przeciwnym razie nie zostanie uwzględniony.

Należy pamiętać, że jeśli utworzysz bibliotekę importu w ramach wstępnego kroku przed utworzeniem biblioteki. dll, musisz przekazać ten sam zestaw plików obiektów podczas kompilowania biblioteki.

## <a name="see-also"></a>Zobacz także

[Praca z bibliotekami importu i plikami eksportu](working-with-import-libraries-and-export-files.md)
