---
title: Literały ciągu języka C
ms.date: 08/31/2018
helpviewer_keywords:
- string literals, syntax
- strings [C++], string literals
- literal strings, C
ms.assetid: 4b05523e-49a2-4900-b21a-754350af3328
ms.openlocfilehash: 31028b51b8010dd7e598ca5e635a35562379bf40
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152316"
---
# <a name="c-string-literals"></a>Literały ciągu języka C

"Literału ciągu" to sekwencja znaków z zestawu ujęty w podwójny cudzysłów znaków źródła (**""**). Literały ciągów są używane do reprezentowania sekwencji znaków, które, razem tworzą ciąg zakończony znakiem null. Należy zawsze prefiks literałów ciągów dwubajtowych literą **L**.

## <a name="syntax"></a>Składnia

*literał ciągu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**"** *s char sekwencji*<sub>zoptymalizowany pod kątem</sub> **"**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**L"** *s char sekwencji*<sub>zoptymalizowany pod kątem</sub> **"**

*s-char-sequence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*s-char*

&nbsp;&nbsp;&nbsp;&nbsp;*s char sekwencji* *s-char*

*s-char*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Każdy członek znak źródłowy zestawu z wyjątkiem podwójny cudzysłów ("), ukośnika odwrotnego (\\), lub znak nowego wiersza<br/>

&nbsp;&nbsp;&nbsp;&nbsp;*escape-sequence*

## <a name="remarks"></a>Uwagi

W poniższym przykładzie przedstawiono prosty literał ciągu:

```C
char *amessage = "This is a string literal.";
```

Escape, wszystkie kody w [sekwencje ucieczki](../c-language/escape-sequences.md) tabeli są prawidłowe w literałach ciągu. Do reprezentowania podwójny cudzysłów w literale ciągu, użyj sekwencji unikowej  **\\"**. Pojedynczy cudzysłów (**"**) może być przedstawiany bez sekwencji unikowej. Ukośnik odwrotny (**\\**) musi występować ukośnik odwrotny, po drugim (**\\\\**), gdy pojawia się wewnątrz ciągu. Ukośnik odwrotny znajduje się na końcu wiersza i zawsze jest interpretowany jako znak kontynuacji wiersza.

## <a name="see-also"></a>Zobacz także

[Elementy języka C](../c-language/elements-of-c.md)
