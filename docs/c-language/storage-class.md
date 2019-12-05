---
title: Klasa magazynu
ms.date: 11/04/2016
helpviewer_keywords:
- linkage [C++], external
- function storage class
- function specifiers, storage class
- storage classes
- Microsoft-specific storage classes
- external linkage, storage-class specifiers
- static storage class specifiers
ms.assetid: 39a79ba6-edf5-42b6-8e45-f94227603dd6
ms.openlocfilehash: aa6e977b3aa03b5f08901cfa8b0abe1b4046e72d
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857011"
---
# <a name="storage-class"></a>Klasa magazynu

Specyfikator klasy magazynowania w definicji funkcji daje funkcję `extern` lub **statyczną** klasę magazynu.

## <a name="syntax"></a>Składnia

*definicja funkcji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;deklarator, *specyfikatory deklaracji*<sub>opt</sub> *-SEQ*<sub>opt</sub> *deklaracji-list*<sub>opt</sub> *złożonej-instrukcja*

atrybut \* / *-SEQ* jest \*em specyficznym dla firmy Microsoft /

*specyfikatory deklaracji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklaracji*<sub></sub> *specyfikatora klasy magazynu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklaracji*<sub></sub> *specyfikatora typu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklaracji*<sub></sub> *kwalifikatora typu*

*specyfikator klasy magazynu*:/\* dla definicji funkcji \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**extern**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**static**

Jeśli definicja funkcji nie zawiera *specyfikatora klasy magazynu*, domyślną klasą magazynu jest `extern`. Można jawnie zadeklarować funkcję jako `extern`, ale nie jest to wymagane.

Jeśli deklaracja funkcji zawiera `extern`*specyfikatora klasy magazynu* , identyfikator ma takie samo powiązanie jak wszelka widoczna deklaracja identyfikatora z zakresem pliku. Jeśli nie ma żadnej widocznej deklaracji z zakresem pliku, identyfikator ma powiązania zewnętrzne. Jeśli identyfikator ma zakres pliku i brak *specyfikatora klasy magazynu*, identyfikator ma powiązania zewnętrzne. Powiązania zewnętrzne oznaczają, że każde wystąpienie identyfikatora oznacza ten sam obiekt lub funkcję. Aby uzyskać więcej informacji na temat powiązania i zakresu plików, zobacz [okres istnienia, zakres, widoczność i połączenie](../c-language/lifetime-scope-visibility-and-linkage.md) .

Deklaracje funkcji o zakresie bloku ze specyfikatorem klasy magazynu innym niż `extern`.

Funkcja z klasą magazynu **static** jest widoczna tylko w pliku źródłowym, w którym jest zdefiniowana. Wszystkie inne funkcje, niezależnie od tego, czy posiadają klasę magazynu `extern` jawnie lub niejawnie, są widoczne we wszystkich plikach z kodem źródłowym w programie. Jeśli wymagana jest Klasa magazynu **statycznego** , musi być zadeklarowana w pierwszym wystąpieniu deklaracji (jeśli istnieje) funkcji i w definicji funkcji.

**Microsoft Specific**

Po włączeniu rozszerzeń Microsoft funkcja oryginalnie zadeklarowana bez klasy magazynu (lub z klasą `extern` Storage) ma określoną klasę magazynu **statycznego** , jeśli definicja funkcji znajduje się w tym samym pliku źródłowym, a definicja jawnie określa **statyczną** klasę magazynu.

Podczas kompilacji z opcją kompilatora /Ze, funkcje zadeklarowane wewnątrz bloku za pomocą słowa kluczowego `extern` mają globalną widoczność. Nie ma to zastosowania podczas kompilowania z opcją /Za. Na tej funkcji nie można polegać, jeżeli trzeba uwzględnić przenośność kodu źródłowego.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Definicje funkcji języka C](../c-language/c-function-definitions.md)
