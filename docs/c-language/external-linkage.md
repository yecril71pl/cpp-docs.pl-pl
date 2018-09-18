---
title: Połączenie zewnętrzne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- linkage [C++], external
- external linkage, about external linkage
- external linkage
ms.assetid: a6f8ea69-b405-4cdd-bf12-ad5462b73183
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: be268dbc153ad0bb140a2adfcfd8ec6385716c48
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027566"
---
# <a name="external-linkage"></a>Połączenie zewnętrzne

Jeśli nie są używane w pierwszej deklaracji na poziomie zakresu pliku dla identyfikatora **statyczne** Specyfikator klasy magazynowania, obiekt ma powiązania zewnętrzne.

Jeśli nie ma deklarację identyfikatora dla funkcji *storage-class-specifier*, połączenie jest określane dokładnie tak, jakby zostały zgłoszone za pomocą *storage-class-specifier* `extern`. Jeśli deklaracja identyfikatora obiektu ma zakres pliku a nie *storage-class-specifier*, połączenie jest zewnętrzny.

Identyfikator nazwy za pomocą zewnętrznego powiązania wyznacza tej samej funkcji lub obiektu danych jako nie żadnej innej deklaracji dla tej samej nazwie, za pomocą zewnętrznego powiązania. Dwie deklaracje może być w tej samej jednostce translacji, czy w jednostkach różnych tłumaczeń. Jeśli obiekt lub funkcja również ma globalny okres istnienia, obiekt lub funkcja jest współużytkowana przez całego programu.

## <a name="see-also"></a>Zobacz też

[Użycie zewnętrznie w celu określenia powiązania](../cpp/using-extern-to-specify-linkage.md)