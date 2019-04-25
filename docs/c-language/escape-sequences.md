---
title: Sekwencje unikowe
ms.date: 11/04/2016
helpviewer_keywords:
- "\r escape sequence"
- double backslash
- horizontal-tab 	 escape sequence
- (') single quotation mark
- "bell character \a escape sequence"
- escape sequences
- hexadecimal escape sequence
- carriage returns
- tab 	 escape sequence
- "\f escape sequence"
- quotation marks, single
- "formfeed \f escape sequence"
- "\v escape sequence"
- control character escape sequences
- " symbol in escape sequences"
- octal escape sequence
- escape characters
- "newline character \n escape sequence"
- nongraphic control characters
- question mark, literal
- "\n escape sequence"
- "vertical tab \v escape sequence"
- "\a escape sequence"
- '? symbol'
- '? symbol, escape sequence character'
- "	 escape sequence"
- backspace escape sequence
ms.assetid: 5aef377f-a76c-4d5c-aa04-8308758ad6a8
ms.openlocfilehash: 9aeb8ca549cce8bddbf5d6ddadb6292c05f573d5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233949"
---
# <a name="escape-sequences"></a>Sekwencje unikowe

Znak kombinacji składających się z ukośnika odwrotnego (**\\**) następują litery lub przy użyciu kombinacji cyfr są nazywane "sekwencje unikowe." Do reprezentowania znaku nowego wiersza, pojedynczy cudzysłów lub niektórych innych znaków w stałej znakowej, należy użyć sekwencji ucieczki. Sekwencja unikowa jest traktowany jako pojedynczy znak i dlatego jest nieprawidłowa w przypadku stałej znakowej.

Sekwencje unikowe są zwykle używane do określ akcje, takie jak znaki powrotu karetki i klawisz tab, przemieszczania na terminale i drukarki. Służą one również zapewnienie literału reprezentacje niedrukowalne znaki i znaki, które zwykle mają specjalne znaczenie, takich jak podwójny cudzysłów (**"**). W poniższej tabeli wymieniono sekwencje wyjścia ANSI i ich znaczenie.

Należy pamiętać, że znak zapytania, poprzedzone znakiem ukośnika odwrotnego (**\\?**) określa literału znaku zapytania w przypadkach, w którym sekwencja znaków może być błędnie zinterpretowana jako trójznaku. Zobacz [Trójznaków](../c-language/trigraphs.md) Aby uzyskać więcej informacji.

### <a name="escape-sequences"></a>Sekwencje unikowe

|Sekwencja unikowa|Reprezentuje|
|---------------------|----------------|
|**\a**|Dzwonek (alert)|
|**\b**|Backspace|
|**\f**|Wysuw strony|
|**\n**|Nowy wiersz|
|**\r**|Powrót karetki|
|**\t**|tabulator poziomy|
|**\v**|tabulator pionowy|
|**\\'**|Znak pojedynczego cudzysłowu|
|**\\"**|Podwójny cudzysłów|
|**\\\\**|Ukośnik odwrotny|
|**\\?**|Literał znaku zapytania|
|**\\** *ooo*|Znak ASCII w ósemkowy|
|**\x** *hh*|Znak ASCII w zapisie szesnastkowym|
|**\x** *hhhh*|Znak Unicode w formacie szesnastkowym, jeśli ta sekwencja ucieczki jest używana w stała dwubajtowego znaku lub literał ciągu znaków Unicode.<br /><br /> Na przykład `WCHAR f = L'\x4e00'` lub `WCHAR b[] = L"The Chinese character for one is \x4e00"`.|

**Microsoft Specific**

Jeśli ukośnik odwrotny poprzedza znak, który nie jest widoczna w tabeli, kompilator obsługuje niezdefiniowane znak jako sam znak. Na przykład `\c` jest traktowany jako `c`.

**END specyficzny dla Microsoft**

Sekwencje unikowe umożliwiają wysyłanie Niegraficzne znaki kontrolne na urządzeniu. Na przykład znak ESC (**\033**) jest często używany jako pierwszy znak polecenia sterowania terminal lub drukarki. Niektóre sekwencje ucieczki są specyficzne dla urządzenia. Na przykład karta w pionie i Wysuw strony sekwencje unikowe (**\v** i **\f**) nie wpływają na ekranie wyników, ale wykonują operacje odpowiednich drukarek.

Możesz również użyć ukośnik odwrotny (**\\**) jako znak kontynuacji. Gdy nowy wiersz znaków (odpowiednik naciskając klawisz ENTER) od razu następuje po odwrotnym ukośniku, kompilator ignoruje ukośnik odwrotny i znak nowego wiersza i traktuje następny wiersz jako część poprzedniego wiersza. Jest to przydatne głównie dla definicje preprocesora więcej niż jeden wiersz. Na przykład:

```
#define assert(exp) \
( (exp) ? (void) 0:_assert( #exp, __FILE__, __LINE__ ) )
```

## <a name="see-also"></a>Zobacz także

[Stałe znakowe języka C](../c-language/c-character-constants.md)
