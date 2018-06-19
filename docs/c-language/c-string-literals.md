---
title: Literały ciągu języka C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- string literals, syntax
- strings [C++], string literals
- literal strings, C
ms.assetid: 4b05523e-49a2-4900-b21a-754350af3328
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 303ad83c5e366f32a99a501a58b168ef25adbb42
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32382786"
---
# <a name="c-string-literals"></a>Literały ciągu języka C
"Literału ciągu" jest sekwencji znaków z zestawu ujęty w podwójnym cudzysłowie znaków źródła (**""**). Literały ciągu są używane do reprezentowania sekwencji znaków, które, razem tworzą ciąg znaków zakończony znakiem null. Należy zawsze prefiksu całej literały z literą **L**.  
  
## <a name="syntax"></a>Składnia  
 *literał ciągu*:  
 **"** *s char sekwencji* opt **"**  
  
 **L"** *s char sekwencji* opt **"**  
  
 *s char sekwencji*:  
 *s char*  
  
 *s char sekwencji s-char*  
  
 *s char*:  
 Każdy członek znak źródłowy ustawić z wyjątkiem podwójnego cudzysłowu ("), ukośnik odwrotny (\\), lub znakiem nowego wiersza  
  
 *sekwencja specjalna*  
  
 W poniższym przykładzie jest proste literał ciągu:  
  
```  
char *amessage = "This is a string literal.";  
```  
  
 Wszystkie wyjścia kody w [sekwencji unikowych](../c-language/escape-sequences.md) tabeli są prawidłowe w literałach ciągu. Do reprezentowania podwójny cudzysłów w literale ciągu, użyj sekwencji ucieczki  **\\"**. Znak pojedynczego cudzysłowu (**"**) może być reprezentowany bez sekwencji ucieczki. Kreska ułamkowa odwrócona (**\\**) musi występować z drugiego ukośnik odwrotny (**\\\\**) po wyświetleniu ciągu. Na końcu wiersza pojawi się ukośnikiem, jest zawsze interpretowane jako znak kontynuacji wiersza.  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy języka C](../c-language/elements-of-c.md)