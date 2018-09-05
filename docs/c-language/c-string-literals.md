---
title: Literały ciągu języka C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/31/2018
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
ms.openlocfilehash: f87b8ce4c8270b8f0d22c2396358e8e1118a4bbd
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43765056"
---
# <a name="c-string-literals"></a>Literały ciągu języka C

"Literału ciągu" to sekwencja znaków z zestawu ujęty w podwójny cudzysłów znaków źródła (**""**). Literały ciągów są używane do reprezentowania sekwencji znaków, które, razem tworzą ciąg zakończony znakiem null. Należy zawsze prefiks literałów ciągów dwubajtowych literą **L**.

## <a name="syntax"></a>Składnia

*literał ciągu*:  
&nbsp;&nbsp;&nbsp;&nbsp;**"** *s char sekwencji*<sub>zoptymalizowany pod kątem</sub> **"**  
&nbsp;&nbsp;&nbsp;&nbsp;**L"** *s char sekwencji*<sub>zoptymalizowany pod kątem</sub> **"**

*s char sekwencji*:  
&nbsp;&nbsp;&nbsp;&nbsp;*s-char*  
&nbsp;&nbsp;&nbsp;&nbsp;*s char sekwencji* *s-char*

*s-char*:  
&nbsp;&nbsp;&nbsp;&nbsp;Każdy członek znak źródłowy zestawu z wyjątkiem podwójny cudzysłów ("), ukośnika odwrotnego (\\), lub znak nowego wiersza  
&nbsp;&nbsp;&nbsp;&nbsp;*Sekwencja unikowa*

## <a name="remarks"></a>Uwagi

W poniższym przykładzie przedstawiono prosty literał ciągu:

```C
char *amessage = "This is a string literal.";
```

Escape, wszystkie kody w [sekwencje ucieczki](../c-language/escape-sequences.md) tabeli są prawidłowe w literałach ciągu. Do reprezentowania podwójny cudzysłów w literale ciągu, użyj sekwencji unikowej  **\\"**. Pojedynczy cudzysłów (**"**) może być przedstawiany bez sekwencji unikowej. Ukośnik odwrotny (**\\**) musi występować ukośnik odwrotny, po drugim (**\\\\**), gdy pojawia się wewnątrz ciągu. Ukośnik odwrotny znajduje się na końcu wiersza i zawsze jest interpretowany jako znak kontynuacji wiersza.

## <a name="see-also"></a>Zobacz też

[Elementy języka C](../c-language/elements-of-c.md)  
