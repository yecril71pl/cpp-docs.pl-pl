---
title: Korzystanie z biblioteki importowanej oraz pliku eksportowanego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- circular exports
- import libraries, using
- export files
ms.assetid: 2634256a-8aa5-4495-8c9e-6cde10e4ed76
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 77157ae9404e1d64aec34c897af7564511f275f8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717252"
---
# <a name="using-an-import-library-and-export-file"></a>Korzystanie z biblioteki importowanej oraz pliku eksportowanego

Kiedy program do innego programu, który także importowanie elementów z eksportuje (plik wykonywalny lub biblioteka DLL), lub jeśli więcej niż dwa programy wyeksportować do i zaimportować od siebie nawzajem, poleceń do łączenia tych programów należy uwzględnić eksporty cykliczne.

W sytuacji braku eksporty cykliczne podczas konsolidacji program, który używa eksportuje z innego programu, należy określić bibliotekę importu eksportowania programu. Bibliotekę importu eksportowania programu jest tworzony, gdy możesz połączyć eksportowania programu. W związku z tym należy połączyć eksportowania programu przed programem importowania. Na przykład, jeśli TWO.dll importowania z ONE.dll, musisz najpierw połączyć ONE.dll i pobrać bibliotekę importowaną ONE.lib. Następnie określasz ONE.lib podczas łączenia TWO.dll. Gdy program łączący tworzy TWO.dll, również tworzy bibliotekę importów, TWO.lib. Za pomocą TWO.lib łączenie programów, które importować z TWO.dll.

Jednakże w przypadku eksportu cykliczne nie jest możliwych do łączenia wszystkich programów współzależne przy użyciu bibliotek importu z innych programów. W przykładzie, o których wspomniano, jeśli TWO.dll Eksportuje również ONE.dll, nie istnieje biblioteki importu TWO.dll dopiero po ONE.dll jest połączony. Jeśli istnieją eksporty cykliczne, należy użyć biblioteki do tworzenia biblioteki importu i eksportu plik dla jednego z programów.

Aby rozpocząć, wybierz jedną z programów, w którym można uruchomić biblioteki. W poleceniu LIB wyświetlić listę wszystkich obiektów i bibliotek programu, a następnie określ /DEF. Jeśli program używa pliku .def lub specyfikacji/Export, określić również.

Po utworzeniu bibliotekę importu (.lib) i plik eksportu (.exp) dla programu przy użyciu biblioteki importu podczas łączenia program lub programy. LINK tworzy bibliotekę importu dla każdego eksportu programu, który kompiluje je. Na przykład jeśli uruchomisz LIB obiektów i eksportowanie na ONE.dll utworzysz ONE.lib i ONE.exp. Teraz możesz używać ONE.lib podczas łączenia TWO.dll; w tym kroku również tworzy bibliotekę importu TWO.lib.

Na koniec połączyć program, który rozpoczął za pomocą. W poleceniu łącze Określ obiektów i bibliotek programu pliku .exp, które LIB utworzone dla programu i bibliotekę importowaną lub biblioteki eksportów używanych przez program. Aby kontynuować w przykładzie, polecenie LINK dla ONE.dll zawiera ONE.exp i TWO.lib, a także obiektów i bibliotek, które bardziej szczegółowo ONE.dll. Nie określaj pliku .def lub specyfikacji/Export w poleceniu łącze; nie są one potrzebne, ponieważ definicje eksportu są zawarte w pliku .exp. Gdy łączysz się przy użyciu pliku .exp, łącze nie tworzy bibliotekę importu, ponieważ przyjęto założenie, że jedna została utworzona podczas tworzenia pliku .exp.

## <a name="see-also"></a>Zobacz też

[Praca z bibliotekami importowanymi oraz plikami eksportowanymi](../../build/reference/working-with-import-libraries-and-export-files.md)