---
title: Przy użyciu biblioteki importowanej oraz pliku eksportowanego | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 946ef702d17762e6771bad206d0bfa682a61055e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378600"
---
# <a name="using-an-import-library-and-export-file"></a>Korzystanie z biblioteki importowanej oraz pliku eksportowanego
Kiedy program (plik wykonywalny lub biblioteka DLL) eksportuje do innego programu, który importuje go także z lub jeśli więcej niż dwa programy wyeksportować do i zaimportować od siebie, poleceń połączyć tych programów należy uwzględnić eksporty cykliczne.  
  
 W sytuacji braku eksporty cykliczne gdy eksportuje łączenie program, który korzysta z innego programu, należy określić bibliotekę importu eksportowanie programu. Bibliotekę importu programu eksportowanie jest tworzony po połączeniu programu eksportowanie. W związku z tym należy połączyć program eksportowanie przed programem importowania. Na przykład, jeśli TWO.dll importowania z ONE.dll, należy najpierw pobrać biblioteki importu ONE.lib i łącza ONE.dll. Następnie zostanie ONE.lib podczas łączenia TWO.dll. Gdy konsolidator tworzy TWO.dll, tworzy również Importuj biblioteki TWO.lib. Za pomocą TWO.lib łączenie programów, które importowanego TWO.dll.  
  
 Jednakże w przypadku eksportowania cykliczne nie jest możliwe do połączenia wszystkich programów współzależne przy użyciu biblioteki importu z innych programów. W przykładzie już wspomniano, jeśli TWO.dll Eksportuje również ONE.dll, bibliotekę importu TWO.dll nie istnieje jeszcze po ONE.dll jest połączony. Jeśli istnieją eksporty cykliczne, należy użyć do tworzenia biblioteki importu i eksportu pliku dla jednego z programów LIB.  
  
 Aby rozpocząć, wybierz jeden z programów, na którym ma być uruchamiany LIB. W poleceniu LIB wyświetlić listę wszystkich obiektów i bibliotek programu i określ /DEF. Jeśli program używa plik .def lub specyfikacji/Export, określić również.  
  
 Po utworzeniu biblioteki importowanej (lib) oraz pliku eksportu (.exp) dla programu, użyj biblioteki importu podczas łączenia program lub programy. ŁĄCZE tworzy bibliotekę importu każdego eksportowanie programu kompilacjach. Na przykład po uruchomieniu LIB na obiekty i eksportuje dla ONE.dll tworzenia ONE.lib i ONE.exp. Teraz możesz używać ONE.lib podczas łączenia TWO.dll; Ten krok tworzy także biblioteki importu TWO.lib.  
  
 Na koniec połączyć program, który użytkownik rozpoczął. W poleceniu łącze określ obiekty i bibliotek programu pliku .exp LIB utworzony dla programu i Importuj biblioteki lub biblioteki eksportów używanych przez program. Kontynuując przykład polecenia łącze do ONE.dll zawiera ONE.exp i TWO.lib, a także obiekty i bibliotek, które wchodzą w ONE.dll. Nie określaj plik .def lub specyfikacji/Export w poleceniu łącze; nie są one potrzebne, ponieważ definicje eksportu są zawarte w pliku .exp. Po połączeniu się przy użyciu pliku .exp, LINK nie powoduje utworzenia biblioteki importowanej, ponieważ przyjęto założenie, że jeden został utworzony podczas tworzenia pliku .exp.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z bibliotekami importowanymi oraz plikami eksportowanymi](../../build/reference/working-with-import-libraries-and-export-files.md)