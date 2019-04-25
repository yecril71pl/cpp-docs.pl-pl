---
title: Operatory przyrostka
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], postfix
- postfix operators
ms.assetid: 76260011-1624-484e-8bef-72ae7ab556cc
ms.openlocfilehash: a86ede25feeaee3a9fb1c6b146cf9667b85c0c2f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232250"
---
# <a name="postfix-operators"></a>Operatory przyrostka

Operatory przyrostkowe ma najwyższy priorytet (najbardziej restrykcyjne metody powiązania) obliczania wyrażeń.

## <a name="syntax"></a>Składnia

*postfix-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenia podstawowe*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **[**  *expression*  **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażeniem przyrostkowym* **(** *argument-expression-list*<sub>zoptymalizowany pod kątem</sub> **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażeniem przyrostkowym* **.**  *Identyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażeniem przyrostkowym* **->** *identyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażeniem przyrostkowym*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażeniem przyrostkowym*  **--**

Operatory na tym poziomie pierwszeństwa indeksy dolne tablicy, wywołania funkcji, struktury i Unii członków i zwiększenie przyrostkowe i operatory dekrementacji.

## <a name="see-also"></a>Zobacz także

[Operatory języka C](../c-language/c-operators.md)
