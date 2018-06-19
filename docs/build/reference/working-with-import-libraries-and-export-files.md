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
ms.openlocfilehash: bc2e5b6b1f2a459d7a00e48ff1aaafff38803871
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377935"
---
# <a name="working-with-import-libraries-and-export-files"></a>Praca z bibliotekami importowanymi oraz plikami eksportowanymi
LIB z opcją/DEF służy do tworzenia biblioteki importowanej oraz pliku eksportu. ŁĄCZE używa pliku eksportu do tworzenia programu, który zawiera eksportuje (zazwyczaj biblioteki dołączanej (dynamicznie DLL)) i używa biblioteki importu można rozpoznać odwołania do tych eksportu w innych programów.  
  
 Należy pamiętać, że w przypadku utworzenia biblioteki importu w krok wstępny, przed utworzeniem sieci dll, należy podać ten sam zestaw plików obiektów podczas tworzenia biblioteki dll, jako przekazaną podczas tworzenia biblioteki importu.  
  
 W większości sytuacji nie trzeba używać LIB do tworzenia biblioteki importu. Po połączeniu programu (plik wykonywalny lub biblioteka DLL) zawierającego eksportuje łącze automatycznie tworzy biblioteki importowanej opisujący eksportu. Później po połączeniu program, który odwołuje się do tych eksportu, określ bibliotekę importu.  
  
 Jednak gdy eksporty biblioteki DLL do programu, który importuje go także z, czy bezpośrednio lub pośrednio, możesz korzystać LIB można utworzyć jedną z biblioteki importu. Gdy LIB tworzy bibliotekę importowaną, również tworzy plik eksportu. Podczas łączenia z jednej z bibliotek DLL należy użyć pliku eksportu.  
  
## <a name="see-also"></a>Zobacz też  
 [LIB — dokumentacja](../../build/reference/lib-reference.md)