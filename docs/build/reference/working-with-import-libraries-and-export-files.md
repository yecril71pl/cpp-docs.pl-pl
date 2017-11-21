---
title: Praca z bibliotekami importowanymi oraz plikami eksportowanymi | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- LIB [C++], /DEF option
- import libraries
- LIB [C++], import libraries and export files
- export files
- import libraries, creating
ms.assetid: d8175596-9773-4c2f-959d-b05b065a5161
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a78f6e4c7cdb5dbd25354d93d9bafc2892098c7d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="working-with-import-libraries-and-export-files"></a>Praca z bibliotekami importowanymi oraz plikami eksportowanymi
LIB z opcją/DEF służy do tworzenia biblioteki importowanej oraz pliku eksportu. ŁĄCZE używa pliku eksportu do tworzenia programu, który zawiera eksportuje (zazwyczaj biblioteki dołączanej (dynamicznie DLL)) i używa biblioteki importu można rozpoznać odwołania do tych eksportu w innych programów.  
  
 Należy pamiętać, że w przypadku utworzenia biblioteki importu w krok wstępny, przed utworzeniem sieci dll, należy podać ten sam zestaw plików obiektów podczas tworzenia biblioteki dll, jako przekazaną podczas tworzenia biblioteki importu.  
  
 W większości sytuacji nie trzeba używać LIB do tworzenia biblioteki importu. Po połączeniu programu (plik wykonywalny lub biblioteka DLL) zawierającego eksportuje łącze automatycznie tworzy biblioteki importowanej opisujący eksportu. Później po połączeniu program, który odwołuje się do tych eksportu, określ bibliotekę importu.  
  
 Jednak gdy eksporty biblioteki DLL do programu, który importuje go także z, czy bezpośrednio lub pośrednio, możesz korzystać LIB można utworzyć jedną z biblioteki importu. Gdy LIB tworzy bibliotekę importowaną, również tworzy plik eksportu. Podczas łączenia z jednej z bibliotek DLL należy użyć pliku eksportu.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do biblioteki LIB](../../build/reference/lib-reference.md)