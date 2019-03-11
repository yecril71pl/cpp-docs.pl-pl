---
title: Zgodność ANSI-C
ms.date: 11/04/2016
f1_keywords:
- Ansi
helpviewer_keywords:
- underscores, leading
- compatibility [C++], ANSI C
- compliance with ANSI C
- conventions [C++], Microsoft extensions
- underscores
- naming conventions [C++], Microsoft library
- ANSI [C++], C standard
- Microsoft extensions naming conventions
ms.assetid: 6be271bf-eecf-491a-a928-0ee2dd60e3b9
ms.openlocfilehash: 7a4462e84ec01bd236849c6aed024b636b315243
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57742824"
---
# <a name="ansi-c-compliance"></a>Zgodność ANSI-C

Konwencja nazewnictwa dla wszystkich identyfikatorów specyficzne dla firmy Microsoft w systemie czasu wykonywania (na przykład funkcje, makra, stałe, zmienne i definicje typów) jest standardem ANSI. W tej dokumentacji każda funkcja środowiska wykonawczego, która następuje standardy ANSI/ISO C podano jako zgodny ze standardem ANSI. Aplikacje zgodne z ANSI, należy używać tylko tych funkcji zgodne z ANSI.

Nazwy funkcji specyficznych dla firmy Microsoft i zmienne globalne rozpoczynają się od jednego podkreślenia. Te nazwy mogą zostać zastąpione tylko lokalnie w zakresie kodu. Na przykład, gdy zostaną umieszczone pliki nagłówkowe środowiska wykonawczego firmy Microsoft, możesz nadal lokalnie zastąpić funkcji specyficzne dla firmy Microsoft o nazwie `_open` przez zadeklarowanie zmiennej lokalnej o tej samej nazwie. Jednak nie można użyć tej nazwy własnego globalnej funkcji lub zmienna globalna.

Nazwy makra specyficzne dla firmy Microsoft i stałych manifestu rozpocząć z dwoma podkreśleniami lub pojedynczego wiodącego podkreślnika bezpośrednio po nim wielkiej litery. Zakres tych identyfikatorów jest bezwzględna. Na przykład nie można użyć identyfikatora specyficzne dla firmy Microsoft **_UPPER** z tego powodu.

## <a name="see-also"></a>Zobacz także

[Zgodność](../c-runtime-library/compatibility.md)
