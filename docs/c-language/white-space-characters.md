---
title: Białe znaki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- white space, characters
- characters, white space
ms.assetid: 030ccbdc-2db3-4dd0-88c8-f5c2669ddebf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3aa487ee277954470cdd8b16f9f64f465c195897
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055705"
---
# <a name="white-space-characters"></a>Znak odstępu

Miejsca, karta, wysuwu wiersza, powrotu karetki, Wysuw strony, kartę w pionie i znaki nowego wiersza są nazywane "białe znaki", ponieważ służą one tę samą funkcję co spacji między wyrazami i wierszy na stronie wydruku — mogą ułatwić odczytywanie. Tokeny są rozdzielone (ograniczone), spacji i innych tokenów, takich jak operatory i znaki interpunkcyjne. Podczas analizowania kodu, kompilator języka C ignoruje znaki odstępu, chyba, że korzystasz z nich jako separatory lub składniki stałe znakowe i literały ciągów znaków. Aby zwiększyć czytelność program, należy użyć białe znaki. Należy pamiętać, że kompilator traktuje komentarze jako biały znak.

## <a name="see-also"></a>Zobacz też

[Tokeny języka C](../c-language/c-tokens.md)