---
title: Praca z bibliotekami importowanymi oraz plikami eksportowanymi
ms.date: 11/04/2016
helpviewer_keywords:
- LIB [C++], /DEF option
- import libraries
- LIB [C++], import libraries and export files
- export files
- import libraries, creating
ms.assetid: d8175596-9773-4c2f-959d-b05b065a5161
ms.openlocfilehash: 6f6f2d5c48c63ba6d8a8a7f67a98b949b32a8afa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316525"
---
# <a name="working-with-import-libraries-and-export-files"></a>Praca z bibliotekami importowanymi oraz plikami eksportowanymi

LIB z opcją/DEF służy do tworzenia biblioteki importowanej oraz pliku eksportu. Używa łącze Stwórz program, który zawiera plik eksportu eksportuje (zwykle dołączana dynamicznie biblioteka (DLL)) i wykorzystuje bibliotekę importowaną do rozpoznawania odwołań do tych eksportu w innych programach.

Należy pamiętać, że jeśli tworzysz biblioteki importu w krok wstępny, przed utworzeniem usługi .dll, należy przekazać ten sam zestaw plików obiektów podczas tworzenia pliku .dll, jako zakończony powodzeniem w podczas kompilowania biblioteki importowanej.

W większości przypadków nie trzeba używać biblioteki do tworzenia biblioteki importu. Podczas łączenia program (plik wykonywalny lub biblioteka DLL), który zawiera eksporty LINK automatycznie tworzy bibliotekę importu, który opisuje polecenie eksportuje. Później połączysz program, który odwołuje się do tych eksporty określ bibliotekę importowaną.

Jednak gdy eksporty biblioteki DLL do programu, który także importowanie elementów z, czy bezpośrednio lub pośrednio, należy użyć LIB utworzenie jednego z bibliotekami importowanymi. Gdy LIB tworzy bibliotekę importu, również tworzy plik eksportu. Podczas łączenia jednej z bibliotek DLL, należy użyć pliku eksportu.

## <a name="see-also"></a>Zobacz także

[LIB — dokumentacja](lib-reference.md)
