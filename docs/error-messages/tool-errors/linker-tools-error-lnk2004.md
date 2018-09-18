---
title: Błąd narzędzi konsolidatora LNK2004 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2004
dev_langs:
- C++
helpviewer_keywords:
- LNK2004
ms.assetid: 07645371-e67b-4a2c-b0e0-dde24c94ef7e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ade04a6315a8e0193ac882d795ef416d406c1ddb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100776"
---
# <a name="linker-tools-error-lnk2004"></a>Błąd narzędzi konsolidatora LNK2004

przepełnienie naprawy względem elementu GP pod kątem; krótka sekcja "section" jest za duża lub poza zakresem.

Sekcja była zbyt duża.

Aby rozwiązać ten problem, należy zmniejszyć rozmiar krótka sekcja albo jawnie umieszczenie danych w długich fragmentów za pośrednictwem sekcji #pragma (".sectionname", odczytu, zapisu, długi) i używając `__declspec(allocate(".sectionname"))` na danych definicje i deklaracje.  Na przykład

```
#pragma section(".data$mylong", read, write, long)
__declspec(allocate(".data$mylong"))
char    rg0[1] = { 1 };
char    rg1[2] = { 1 };
char    rg2[4] = { 1 };
char    rg3[8] = { 1 };
char    rg4[16] = { 1 };
char    rg5[32] = { 1 };
```

Można również przenieść dane logicznie pogrupowane w jego własnej strukturę, która będzie Kolekcja danych, które są większe niż 8 bajtów, które kompilator przydzieli w sekcji danych long.  Na przykład

```
// from this...
int     w1  = 23;
int     w2 = 46;
int     w3 = 23*3;
int     w4 = 23*4;

// to this...
struct X {
    int     w1;
    int     w2;
    int     w3;
    int     w4;
} x  = { 23, 23*2, 23*3, 23*4 };

```

Ten błąd występuje błąd krytyczny `LNK1165`.