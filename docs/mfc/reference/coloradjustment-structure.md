---
title: Struktura COLORADJUSTMENT
ms.date: 11/04/2016
f1_keywords:
- COLORADJUSTMENT
helpviewer_keywords:
- COLORADJUSTMENT structure [MFC]
ms.assetid: 67fc4e63-0e0e-4fcb-8c45-aa5ebfefa013
ms.openlocfilehash: 4f25b8241c1862a9c12d405ee5d47d5553dd6e29
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623512"
---
# <a name="coloradjustment-structure"></a>Struktura COLORADJUSTMENT

`COLORADJUSTMENT` Struktury definiuje wartości dostosowanie kolorów, które są używane przez Windows `StretchBlt` i `StretchDIBits` funkcji podczas `StretchBlt` PÓŁTONÓW jest tryb.

## <a name="syntax"></a>Składnia

```
typedef struct  tagCOLORADJUSTMENT {    /* ca */
    WORD caSize;
    WORD caFlags;
    WORD caIlluminantIndex;
    WORD caRedGamma;
    WORD caGreenGamma;
    WORD caBlueGamma;
    WORD caReferenceBlack;
    WORD caReferenceWhite;
    SHORT caContrast;
    SHORT caBrightness;
    SHORT caColorfulness;
    SHORT caRedGreenTint;
} COLORADJUSTMENT;
```

#### <a name="parameters"></a>Parametry

*caSize*<br/>
Określa rozmiar struktury w bajtach.

*caFlags*<br/>
Określa, jak można przygotować obraz danych wyjściowych. Ten element członkowski można ustawić na zero lub dowolną kombinację następujących wartości:

- CA_NEGATIVE Określa, że negacją oryginalny obraz powinien być wyświetlany.

- CA_LOG_FILTER Określa, że funkcja logarytmiczna powinny być stosowane do końcowego gęstość kolory danych wyjściowych. To spowoduje zwiększenie kontrast kolorów, gdy brakuje jasności.

*caIlluminantIndex*<br/>
Określa jasności po stronie źródła światła w ramach której jest wyświetlany obiekt obrazu. Ten element członkowski można ustawić jedną z następujących wartości:

- ILLUMINANT_EQUAL_ENERGY

- ILLUMINANT_A

- ILLUMINANT_B

- ILLUMINANT_C

- ILLUMINANT_D50

- ILLUMINANT_D55

- ILLUMINANT_D65

- ILLUMINANT_D75

- ILLUMINANT_F2

- ILLUMINANT_TURNGSTEN

- ILLUMINANT_DAYLIGHT

- ILLUMINANT_FLUORESCENT

- ILLUMINANT_NTSC

*caRedGamma*<br/>
Określa wartość korekcji gamma n-ty zasilania dla podstawowego czerwony kolorów źródła. Wartość musi należeć do zakresu od 2500 do 65 000. Wartość 10 000 oznacza, że nie korekcji gamma.

*caGreenGamma*<br/>
Określa wartość korekcji gamma n-ty zasilania dla podstawowego zielony kolorów źródła. Wartość musi należeć do zakresu od 2500 do 65 000. Wartość 10 000 oznacza, że nie korekcji gamma.

*caBlueGamma*<br/>
Określa wartość korekcji gamma n-ty zasilania dla podstawowego niebieski kolorów źródła. Wartość musi należeć do zakresu od 2500 do 65 000. Wartość 10 000 oznacza, że nie korekcji gamma.

*caReferenceBlack*<br/>
Określa odwołanie do czarnego kolory źródła. Wszelkie kolorów, które są ciemniejsze od tego, są traktowane jako czarny. Wartość musi należeć do zakresu od 0 do 4000.

*caReferenceWhite*<br/>
Określa odwołanie białe kolorów źródła. Wszelkie kolorów, które są cieńszego niż to są traktowane jako biały. Wartość musi należeć do zakresu od 6000 do 10 000.

*caContrast*<br/>
Określa ilość kontrastu mają być stosowane do obiektu źródłowego. Wartość musi należeć do zakresu od -100 do 100. Wartość 0 oznacza nie dopasowania kontrast.

*caBrightness*<br/>
Określa ilość jasność ma zostać zastosowany do obiektu źródłowego. Wartość musi należeć do zakresu od -100 do 100. Wartość 0 oznacza nie dopasowania Jasność.

*caColorfulness*<br/>
Określa ilość colorfulness ma zostać zastosowany do obiektu źródłowego. Wartość musi należeć do zakresu od -100 do 100. Wartość 0 oznacza nie dopasowania colorfulness.

*caRedGreenTint*<br/>
Określa dopasowania odcień czerwonego lub zielonego, ma zostać zastosowany do obiektu źródłowego. Wartość musi należeć do zakresu od -100 do 100. Liczb dodatnich może dopasować względem czerwieni, a liczby ujemne dopasować względem zieleni. Wartość 0 oznacza nie dopasowania odcień.

## <a name="requirements"></a>Wymagania

**Nagłówek:** wingdi.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDC::GetColorAdjustment](../../mfc/reference/cdc-class.md#getcoloradjustment)

