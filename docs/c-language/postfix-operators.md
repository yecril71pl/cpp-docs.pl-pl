---
title: Operatory przyrostka
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], postfix
- postfix operators
ms.assetid: 76260011-1624-484e-8bef-72ae7ab556cc
ms.openlocfilehash: a86ede25feeaee3a9fb1c6b146cf9667b85c0c2f
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147909"
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
