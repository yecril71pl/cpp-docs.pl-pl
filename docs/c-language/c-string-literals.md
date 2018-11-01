---
title: Literały ciągu języka C
ms.date: 08/31/2018
helpviewer_keywords:
- string literals, syntax
- strings [C++], string literals
- literal strings, C
ms.assetid: 4b05523e-49a2-4900-b21a-754350af3328
ms.openlocfilehash: bd8b49645e34224cbea7e801f197bfbcbc012915
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635629"
---
# <a name="c-string-literals"></a>Literały ciągu języka C

"Literału ciągu" to sekwencja znaków z zestawu ujęty w podwójny cudzysłów znaków źródła (**""**). Literały ciągów są używane do reprezentowania sekwencji znaków, które, razem tworzą ciąg zakończony znakiem null. Należy zawsze prefiks literałów ciągów dwubajtowych literą **L**.

## <a name="syntax"></a>Składnia

*literał ciągu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**"** *s char sekwencji*<sub>zoptymalizowany pod kątem</sub> **"**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**L"** *s char sekwencji*<sub>zoptymalizowany pod kątem</sub> **"**

*s char sekwencji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*s-char*

&nbsp;&nbsp;&nbsp;&nbsp;*s char sekwencji* *s-char*

*s-char*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Każdy członek znak źródłowy zestawu z wyjątkiem podwójny cudzysłów ("), ukośnika odwrotnego (\\), lub znak nowego wiersza<br/>

&nbsp;&nbsp;&nbsp;&nbsp;*Sekwencja unikowa*

## <a name="remarks"></a>Uwagi

W poniższym przykładzie przedstawiono prosty literał ciągu:

```C
char *amessage = "This is a string literal.";
```

Escape, wszystkie kody w [sekwencje ucieczki](../c-language/escape-sequences.md) tabeli są prawidłowe w literałach ciągu. Do reprezentowania podwójny cudzysłów w literale ciągu, użyj sekwencji unikowej  **\\"**. Pojedynczy cudzysłów (**"**) może być przedstawiany bez sekwencji unikowej. Ukośnik odwrotny (**\\**) musi występować ukośnik odwrotny, po drugim (**\\\\**), gdy pojawia się wewnątrz ciągu. Ukośnik odwrotny znajduje się na końcu wiersza i zawsze jest interpretowany jako znak kontynuacji wiersza.

## <a name="see-also"></a>Zobacz też

[Elementy języka C](../c-language/elements-of-c.md)
