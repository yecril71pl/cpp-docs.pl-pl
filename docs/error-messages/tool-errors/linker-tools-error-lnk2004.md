---
title: Błąd narzędzi konsolidatora LNK2004
ms.date: 11/04/2016
f1_keywords:
- LNK2004
helpviewer_keywords:
- LNK2004
ms.assetid: 07645371-e67b-4a2c-b0e0-dde24c94ef7e
ms.openlocfilehash: 37eb01b5dd8266bce34e1a932271d5d9a9d15c52
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50529327"
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