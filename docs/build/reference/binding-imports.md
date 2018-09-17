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
ms.openlocfilehash: 551028999d11379c06d3319f01e882a33ad57936
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705201"
---
# <a name="binding-imports"></a>Powiązywanie importów

Zachowanie konsolidatora domyślne jest do utworzenia tabeli adresów importowania możliwej do wiązania dla bibliotek DLL ładowanych z opóźnieniem. Jeśli biblioteka DLL jest związany, funkcji pomocnika zostanie podjęta próba wykorzystania powiązane informacje, zamiast wywoływać metodę **GetProcAddress** na wszystkich importów odwołania. Jeśli znacznik czasu lub preferowany adres nie pasują załadowanej biblioteki dll, funkcja pomocnika przyjmie tabeli adresów importowania powiązanej jest nieaktualna i będzie kontynuowane tak, jakby nie istnieje.

Jeśli nigdy nie zamierzasz powiązać importów załadowanych z opóźnieniem biblioteki DLL, określając [/opóźnienie](../../build/reference/delay-delay-load-import-settings.md): nobind w wierszu polecenia konsolidatora uniemożliwi tabeli adresów importowania powiązanej jest wygenerowany i korzystanie z nich miejsca w pliku obrazu.

## <a name="see-also"></a>Zobacz też

[Obsługa konsolidatora dla bibliotek DLL załadowanych z opóźnieniem](../../build/reference/linker-support-for-delay-loaded-dlls.md)