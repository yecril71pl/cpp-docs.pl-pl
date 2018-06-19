---
title: Powiązywanie importów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- /DELAY:NOBIND linker option
- DELAY:NOBIND linker option
ms.assetid: bb766038-deb1-41b1-bcbc-29a30e8c1e2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7519fb18ac7f24e79a5f7f664cb35f8eb5b3fd77
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368931"
---
# <a name="binding-imports"></a>Powiązywanie importów
Domyślnym zachowaniem konsolidatora jest utworzyć tabelę adresów importu można powiązać dla biblioteki DLL załadowanych z opóźnieniem. Jeśli plik DLL, który jest powiązany, funkcja pomocnika zostanie podjęta próba wykorzystania powiązane informacje zamiast wywoływać metodę **GetProcAddress** na wszystkich importów do którego istnieje odwołanie. Jeśli znacznik czasu lub preferowany adres nie pasują załadowanej biblioteki dll, funkcja pomocnika przyjmie tabelę adresów importu powiązane jest nieaktualna i będzie kontynuowane tak, jakby nie istnieje.  
  
 Jeśli nie jest planowane powiązać Importy załadowane z opóźnieniem biblioteki DLL, określając [/delay](../../build/reference/delay-delay-load-import-settings.md): nobind w wierszu polecenia konsolidatora uniemożliwi tabelę adresów importu powiązane są generowane i spójniejsze miejsca w pliku obrazu.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa konsolidatora dla bibliotek DLL załadowanych z opóźnieniem](../../build/reference/linker-support-for-delay-loaded-dlls.md)