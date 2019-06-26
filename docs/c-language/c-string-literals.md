---
title: Literały ciągu języka C
ms.date: 08/31/2018
helpviewer_keywords:
- string literals, syntax
- strings [C++], string literals
- literal strings, C
ms.assetid: 4b05523e-49a2-4900-b21a-754350af3328
ms.openlocfilehash: 0df7126efe5a5b2caa3a4fee51465d0dbe892e89
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400583"
---
# <a name="c-string-literals"></a>Literały ciągu języka C

"Literału ciągu" to sekwencja znaków z zestawu ujęty w podwójny cudzysłów znaków źródła ( **""** ). Literały ciągów są używane do reprezentowania sekwencji znaków, które, razem tworzą ciąg zakończony znakiem null. Należy zawsze prefiks literałów ciągów dwubajtowych literą **L**.

## <a name="syntax"></a>Składnia

*literał ciągu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **"** *s char sekwencji*<sub>zoptymalizowany pod kątem</sub> **"**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**L"** *s char sekwencji*<sub>zoptymalizowany pod kątem</sub> **"**

*s-char-sequence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*s-char*

&nbsp;&nbsp;&nbsp;&nbsp;*s char sekwencji* *s-char*

*s-char*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Każdy członek znak źródłowy zestawu z wyjątkiem podwójny cudzysłów ("), ukośnika odwrotnego (\\), lub znak nowego wiersza

&nbsp;&nbsp;&nbsp;&nbsp;*escape-sequence*

## <a name="remarks"></a>Uwagi

W poniższym przykładzie przedstawiono prosty literał ciągu:

```C
char *amessage = "This is a string literal.";
```

Escape, wszystkie kody w [sekwencje ucieczki](../c-language/escape-sequences.md) tabeli są prawidłowe w literałach ciągu. Do reprezentowania podwójny cudzysłów w literale ciągu, użyj sekwencji unikowej  **\\"** . Pojedynczy cudzysłów ( **"** ) może być przedstawiany bez sekwencji unikowej. Ukośnik odwrotny ( **\\** ) musi występować ukośnik odwrotny, po drugim ( **\\\\** ), gdy pojawia się wewnątrz ciągu. Ukośnik odwrotny znajduje się na końcu wiersza i zawsze jest interpretowany jako znak kontynuacji wiersza.

## <a name="see-also"></a>Zobacz także

[Elementy języka C](../c-language/elements-of-c.md)
