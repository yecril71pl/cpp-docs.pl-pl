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

Operatory przyrostkowe mają najwyższy priorytet (najściślejsze wiązanie) podczas obliczania wyrażenia.

## <a name="syntax"></a>Składnia

*wyrażenie przyrostkowe*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie podstawowe*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*przyrostk — wyrażenie*  **[**  *wyrażenie*  **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*przyrostkowe wyrażenie***(***opt-expression-list*<sub>opt</sub> **)**    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie przyrostkowe*  **.**  *identyfikatora*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression***->***Identyfikator* wyrażenia przyrostkowego    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie przyrostkowe*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie przyrostkowe*  **--**

Operatory na tym poziomie pierwszeństwa są indeksami dolnymi tablicy, wywołaniami funkcji, strukturą i elementami członkowskimi Unii oraz przyrostem przyrostkowym i zmniejszeniem.

## <a name="see-also"></a>Zobacz też

[Operatory języka C](../c-language/c-operators.md)
