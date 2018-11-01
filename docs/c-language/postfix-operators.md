---
title: Operatory przyrostka
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], postfix
- postfix operators
ms.assetid: 76260011-1624-484e-8bef-72ae7ab556cc
ms.openlocfilehash: 45f7b67b62657c498bdd9ebcf5d85379cdcdd211
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440707"
---
# <a name="postfix-operators"></a>Operatory przyrostka

Operatory przyrostkowe ma najwyższy priorytet (najbardziej restrykcyjne metody powiązania) obliczania wyrażeń.

## <a name="syntax"></a>Składnia

*wyrażeniem przyrostkowym*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenia podstawowe*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażeniem przyrostkowym***[***wyrażenie***]** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażeniem przyrostkowym***(***argument-expression-list*<sub>zoptymalizowany pod kątem</sub> **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażeniem przyrostkowym***.**  *Identyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażeniem przyrostkowym***->***identyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażeniem przyrostkowym*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażeniem przyrostkowym*  **--**

Operatory na tym poziomie pierwszeństwa indeksy dolne tablicy, wywołania funkcji, struktury i Unii członków i zwiększenie przyrostkowe i operatory dekrementacji.

## <a name="see-also"></a>Zobacz też

[Operatory języka C](../c-language/c-operators.md)