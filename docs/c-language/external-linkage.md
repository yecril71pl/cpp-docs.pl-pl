---
title: Połączenie zewnętrzne
ms.date: 11/04/2016
helpviewer_keywords:
- linkage [C++], external
- external linkage, about external linkage
- external linkage
ms.assetid: a6f8ea69-b405-4cdd-bf12-ad5462b73183
ms.openlocfilehash: 35b0fda1f501755640123f5181454a5c36b7e986
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233744"
---
# <a name="external-linkage"></a>Połączenie zewnętrzne

Jeśli nie są używane w pierwszej deklaracji na poziomie zakresu pliku dla identyfikatora **statyczne** Specyfikator klasy magazynowania, obiekt ma powiązania zewnętrzne.

Jeśli nie ma deklarację identyfikatora dla funkcji *storage-class-specifier*, połączenie jest określane dokładnie tak, jakby zostały zgłoszone za pomocą *storage-class-specifier* `extern`. Jeśli deklaracja identyfikatora obiektu ma zakres pliku a nie *storage-class-specifier*, połączenie jest zewnętrzny.

Identyfikator nazwy za pomocą zewnętrznego powiązania wyznacza tej samej funkcji lub obiektu danych jako nie żadnej innej deklaracji dla tej samej nazwie, za pomocą zewnętrznego powiązania. Dwie deklaracje może być w tej samej jednostce translacji, czy w jednostkach różnych tłumaczeń. Jeśli obiekt lub funkcja również ma globalny okres istnienia, obiekt lub funkcja jest współużytkowana przez całego programu.

## <a name="see-also"></a>Zobacz także

[Użycie zewnętrznie w celu określenia powiązania](../cpp/using-extern-to-specify-linkage.md)
