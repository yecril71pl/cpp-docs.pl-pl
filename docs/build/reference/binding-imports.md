---
title: "Powiązywanie importów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- /DELAY:NOBIND linker option
- DELAY:NOBIND linker option
ms.assetid: bb766038-deb1-41b1-bcbc-29a30e8c1e2a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cd9bee6423c0eea98941331dcff86c002dd4ef9d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="binding-imports"></a>Powiązywanie importów
Domyślnym zachowaniem konsolidatora jest utworzyć tabelę adresów importu można powiązać dla biblioteki DLL załadowanych z opóźnieniem. Jeśli plik DLL, który jest powiązany, funkcja pomocnika zostanie podjęta próba wykorzystania powiązane informacje zamiast wywoływać metodę **GetProcAddress** na wszystkich importów do którego istnieje odwołanie. Jeśli znacznik czasu lub preferowany adres nie pasują załadowanej biblioteki dll, funkcja pomocnika przyjmie tabelę adresów importu powiązane jest nieaktualna i będzie kontynuowane tak, jakby nie istnieje.  
  
 Jeśli nie jest planowane powiązać Importy załadowane z opóźnieniem biblioteki DLL, określając [/delay](../../build/reference/delay-delay-load-import-settings.md): nobind w wierszu polecenia konsolidatora uniemożliwi tabelę adresów importu powiązane są generowane i spójniejsze miejsca w pliku obrazu.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa konsolidatora dla bibliotek DLL załadowanych z opóźnieniem](../../build/reference/linker-support-for-delay-loaded-dlls.md)