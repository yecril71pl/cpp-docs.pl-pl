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
- "form feed \f escape sequence"
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
ms.openlocfilehash: 5de0b5f1a73fcfb6ea0325bea3247ebe4c85d411
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2019
ms.locfileid: "68375825"
---
# <a name="escape-sequences"></a>Sekwencje unikowe

Kombinacje znaków składające się z ukośnika odwrotnego ( **\\** ), po którym następuje litera lub kombinacja cyfr są nazywane "sekwencjami ucieczki". Do reprezentowania znaku nowego wiersza, pojedynczego cudzysłowu lub niektórych innych znaków w stałej znakowej, należy użyć sekwencji unikowych. Sekwencja ucieczki jest traktowana jako pojedynczy znak i dlatego jest ważna jako stała znakowa.

Sekwencje unikowe są zwykle używane do określania akcji, takich jak powrót karetki i ruchy tabulacji na terminalach i drukarkach. Są one również używane do dostarczania literałów niedrukowalnych znaków i znaków, które zwykle mają specjalne znaczenie, takie jak podwójny cudzysłów ( **"** ). W poniższej tabeli wymieniono sekwencje unikowe ANSI i ich znaczenie.

Należy zauważyć, że znak zapytania poprzedzony ukośnikiem odwrotnym ( **\\?** ) określa znak zapytania literału w przypadkach, gdy sekwencja znaków byłaby błędnie interpretowana jako trójznaków. Aby uzyskać więcej informacji, zobacz [trigraphs](../c-language/trigraphs.md) .

### <a name="escape-sequences"></a>Sekwencje unikowe

|Sekwencja unikowa|Reprezentuje|
|---------------------|----------------|
|**\a**|Dzwonek (Alert)|
|**stosuje**|Backspace|
|**\f**|Kanał informacyjny formularza|
|**\n**|Nowy wiersz|
|**\r**|Znak powrotu karetki|
|**\t**|Tabulator poziomy|
|**\v**|Tabulator pionowy|
|**\\'**|Znak pojedynczego cudzysłowu|
|**\\"**|Podwójny cudzysłów|
|**\\\\**|Ukośnik odwrotny|
|**\\?**|Znak zapytania literału|
|**\\** *OOO*|Znak ASCII w notacji ósemkowej|
|**\x** *hh*|Znak ASCII w notacji szesnastkowej|
|**\x** *hhhh*|Znak Unicode w notacji szesnastkowej, jeśli ta sekwencja ucieczki jest używana w stałej znakowej lub literale ciągu Unicode.<br /><br /> Na przykład `WCHAR f = L'\x4e00'` lub `WCHAR b[] = L"The Chinese character for one is \x4e00"`.|

**Microsoft Specific**

Jeśli ukośnik odwrotny poprzedza znak, który nie występuje w tabeli, kompilator obsługuje niezdefiniowany znak jako sam znak. Na przykład, `\c` jest traktowany `c`jako.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

Sekwencje unikowe umożliwiają wysyłanie niegraficznych znaków kontrolnych na urządzenie wyświetlane. Na przykład znak ESC ( **\ 033**) jest często używany jako pierwszy znak polecenia sterowania dla terminalu lub drukarki. Niektóre sekwencje ucieczki to specyficzne dla urządzenia. Na przykład sekwencje unikowe karty pionowej i kanału informacyjnego ( **\v** i **\f**) nie wpływają na dane wyjściowe ekranu, ale wykonują odpowiednie operacje drukarki.

Można również użyć ukośnika odwrotnego ( **\\** ) jako znaku kontynuacji. Gdy znak nowego wiersza (odpowiednik naciskania klawisza powrotu) bezpośrednio następuje po ukośniku odwrotnym, kompilator ignoruje ukośnik odwrotny i znak nowego wiersza i traktuje następny wiersz jako część poprzedniego wiersza. Jest to przydatne głównie w przypadku definicji preprocesora więcej niż jeden wiersz. Na przykład:

```
#define assert(exp) \
( (exp) ? (void) 0:_assert( #exp, __FILE__, __LINE__ ) )
```

## <a name="see-also"></a>Zobacz także

[Stałe znakowe języka C](../c-language/c-character-constants.md)
