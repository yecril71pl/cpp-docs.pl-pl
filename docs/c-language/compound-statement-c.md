---
title: Statement (C) złożona | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- compound statements
- statements, compound
ms.assetid: 32d1bf86-cbbc-42a9-ba3a-1be1c6c7754c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e13f09defccb0aeb3d4ec47cf7cf1678deaee6dd
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43767806"
---
# <a name="compound-statement-c"></a>Instrukcja złożona (C)

Instrukcja złożona (również o nazwie "blok") zwykle jest wyświetlany jako treść innej instrukcji, takich jak **Jeśli** instrukcji. [Deklaracje i typy](../c-language/declarations-and-types.md) opisuje formularza i znaczenie deklaracje, które mogą być wyświetlane na czele instrukcję złożonego.

## <a name="syntax"></a>Składnia

*Compound-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *lista deklaracji*<sub>zoptymalizowany pod kątem</sub> *listy instrukcji*<sub>zoptymalizowany pod kątem</sub> **}**

*Lista deklaracji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista deklaracji* *deklaracji*

*Lista instrukcji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista instrukcji* *— instrukcja*

W przypadku deklaracji one musi występować przed wszystkimi instrukcjami. Zakres każdego identyfikatora zadeklarowane na początku instrukcji złożonej rozciąga się od punktu jego deklaracji na końcu bloku. Może to być widoczna w bloku, chyba że deklaracja tego samego identyfikatora istnieje w wewnętrzny blok.

Identyfikatory w instrukcji złożonej uznaje za **automatycznie** , chyba że jawnie zadeklarowane w przeciwnym razie z **zarejestrować**, **statyczne**, lub `extern`, z wyjątkiem funkcji, który może zawierać tylko `extern`. Można pozostawić wyłączone `extern` specyfikator w deklaracji funkcji i funkcja będzie nadal `extern`.

Magazyn nie jest przydzielany i inicjowanie nie jest dozwolone, jeśli zmienna lub funkcja jest zadeklarowana w instrukcji złożonej z klasą magazynu `extern`. Deklaracja odnosi się do zewnętrznej zmiennej lub funkcji definiowane w innym miejscu.

Zmienne zadeklarowane w bloku z **automatycznie** lub **zarejestrować** — słowo kluczowe są ponownie przydzielane i, jeśli to konieczne, inicjowany każdorazowo wprowadzono złożone wyrażenie. Te zmienne nie są zdefiniowane, po złożone wyrażenie jest został zakończony. Jeśli zmienna zadeklarowana wewnątrz bloku **statyczne** atrybutu, zmienna jest inicjowana, gdy wykonywanie programu rozpoczyna się i przechowuje wartość w całym programie. Zobacz [klasy magazynu](../c-language/c-storage-classes.md) uzyskać informacji na temat **statyczne**.

Ten przykład ilustruje złożonej instrukcji:

```
if ( i > 0 )
{
    line[i] = x;
    x++;
    i--;
}
```

W tym przykładzie Jeśli `i` jest większa niż 0, wszystkie instrukcje wewnątrz instrukcji złożonej zostały wykonane w porządku.

## <a name="see-also"></a>Zobacz też
[Instrukcje](../c-language/statements-c.md)