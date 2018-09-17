---
title: Praca z bibliotekami importowanymi oraz plikami eksportowanymi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- LIB [C++], /DEF option
- import libraries
- LIB [C++], import libraries and export files
- export files
- import libraries, creating
ms.assetid: d8175596-9773-4c2f-959d-b05b065a5161
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 28b4b94025c813ea526964ed6395a2e6af1ac0b9
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721243"
---
# <a name="working-with-import-libraries-and-export-files"></a>Praca z bibliotekami importowanymi oraz plikami eksportowanymi

LIB z opcją/DEF służy do tworzenia biblioteki importowanej oraz pliku eksportu. Używa łącze Stwórz program, który zawiera plik eksportu eksportuje (zwykle dołączana dynamicznie biblioteka (DLL)) i wykorzystuje bibliotekę importowaną do rozpoznawania odwołań do tych eksportu w innych programach.

Należy pamiętać, że jeśli tworzysz biblioteki importu w krok wstępny, przed utworzeniem usługi .dll, należy przekazać ten sam zestaw plików obiektów podczas tworzenia pliku .dll, jako zakończony powodzeniem w podczas kompilowania biblioteki importowanej.

W większości przypadków nie trzeba używać biblioteki do tworzenia biblioteki importu. Podczas łączenia program (plik wykonywalny lub biblioteka DLL), który zawiera eksporty LINK automatycznie tworzy bibliotekę importu, który opisuje polecenie eksportuje. Później połączysz program, który odwołuje się do tych eksporty określ bibliotekę importowaną.

Jednak gdy eksporty biblioteki DLL do programu, który także importowanie elementów z, czy bezpośrednio lub pośrednio, należy użyć LIB utworzenie jednego z bibliotekami importowanymi. Gdy LIB tworzy bibliotekę importu, również tworzy plik eksportu. Podczas łączenia jednej z bibliotek DLL, należy użyć pliku eksportu.

## <a name="see-also"></a>Zobacz też

[LIB — dokumentacja](../../build/reference/lib-reference.md)