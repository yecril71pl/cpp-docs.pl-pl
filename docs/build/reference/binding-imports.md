---
title: Powiązywanie importów
ms.date: 11/04/2016
helpviewer_keywords:
- /DELAY:NOBIND linker option
- DELAY:NOBIND linker option
ms.assetid: bb766038-deb1-41b1-bcbc-29a30e8c1e2a
ms.openlocfilehash: 4058d738b87b69a73e8f18d977be8435a7d96a14
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272926"
---
# <a name="binding-imports"></a>Powiązywanie importów

Zachowanie konsolidatora domyślne jest do utworzenia tabeli adresów importowania możliwej do wiązania dla bibliotek DLL ładowanych z opóźnieniem. Jeśli biblioteka DLL jest związany, funkcji pomocnika zostanie podjęta próba wykorzystania powiązane informacje, zamiast wywoływać metodę **GetProcAddress** na wszystkich importów odwołania. Jeśli znacznik czasu lub preferowany adres nie pasują załadowanej biblioteki dll, funkcja pomocnika przyjmie tabeli adresów importowania powiązanej jest nieaktualna i będzie kontynuowane tak, jakby nie istnieje.

Jeśli nigdy nie zamierzasz powiązać importów załadowanych z opóźnieniem biblioteki DLL, określając [/opóźnienie](delay-delay-load-import-settings.md): nobind w wierszu polecenia konsolidatora uniemożliwi tabeli adresów importowania powiązanej jest wygenerowany i korzystanie z nich miejsca w pliku obrazu.

## <a name="see-also"></a>Zobacz także

[Obsługa konsolidatora dla bibliotek DLL załadowanych z opóźnieniem](linker-support-for-delay-loaded-dlls.md)
