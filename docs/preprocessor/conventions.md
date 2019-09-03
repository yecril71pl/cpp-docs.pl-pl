---
title: Konwencje dokumentów
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor
- preprocessor, conventions
ms.assetid: 469ce448-dc6c-4d0e-ba2b-e2e7a10155e1
ms.openlocfilehash: bb826b879b71edd3631c11a717320cee51c87175
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220372"
---
# <a name="document-conventions"></a>Konwencje dokumentów

Konwencje używają różnych atrybutów czcionki dla różnych składników składni. Symbole i czcionki są następujące:

| Atrybut | Opis |
|---------------|-----------------|
| *nieterminal* | Typ kursywy oznacza nieterminale. |
| **#include** | Terminale w pogrubieniu są literałami zarezerwowanymi i symbolami, które muszą zostać wprowadzone jako pokazane. Znaki w tym kontekście zawsze uwzględniają wielkość liter. |
| <sub>opt</sub> | Nieterminale, po których następuje <sub>wybór</sub> , są zawsze opcjonalne.|
| domyślny krój czcionki | Znaki w zestawie opisany lub wymieniony w tym kroju pisma mogą być używane jako terminale w instrukcjach. |

Jest to dwukropek ( **:** ) po wprowadzeniu definicji przez nieterminala. Definicje alternatywne są wymienione w osobnych wierszach.

W blokach składni kodu te symbole w domyślnym kroju czcionki mają specjalne znaczenie:

| Symbol | Opis |
|---|---|
| \[] | Nawiasy kwadratowe otaczają opcjonalny element. |
| { \| } | Nawiasy klamrowe otoczone alternatywnymi elementami oddzielonymi pionowymi paskami. |
| ... | Wskazuje, że poprzedni wzorzec elementu może być powtórzony. |

W blokach składni kodu przecinki (`,`), kropki`.`(),`;`średniki (),`( )`dwukropek`:`(), nawiasy (), podwójne cudzysłowy (`"`) i pojedyncze cudzysłowy (`'`) są literałami.

## <a name="see-also"></a>Zobacz także

[Podsumowanie gramatyki (CC++/)](../preprocessor/grammar-summary-c-cpp.md)
