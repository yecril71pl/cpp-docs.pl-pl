---
title: Struktura COLORADJUSTMENT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COLORADJUSTMENT
dev_langs:
- C++
helpviewer_keywords:
- COLORADJUSTMENT structure [MFC]
ms.assetid: 67fc4e63-0e0e-4fcb-8c45-aa5ebfefa013
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ffb0ec0233edd968ad121b84f9e1d584a26f3387
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369967"
---
# <a name="coloradjustment-structure"></a>Struktura COLORADJUSTMENT
`COLORADJUSTMENT` Struktury definiuje wartości dostosowania kolorów, które są używane przez system Windows `StretchBlt` i **StretchDIBits** funkcji podczas `StretchBlt` jest tryb **PÓŁTONÓW**.  
  
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
 *caSize*  
 Określa rozmiar struktury w bajtach.  
  
 *caFlags*  
 Określa, jak można przygotować obraz danych wyjściowych. Ten element członkowski może być ustawiony na **NULL** lub dowolną kombinację następujących wartości:  
  
- **CA_NEGATIVE** Określa, że wyświetlane ujemna oryginalnego obrazu.  
  
- **CA_LOG_FILTER** Określa, że funkcja logarytmiczna powinny być stosowane do końcowego gęstość kolory danych wyjściowych. Zwiększy kontrast kolorów gdy jasności jest niskie.  
  
 *caIlluminantIndex*  
 Określa jasności źródła światła, pod którym jest wyświetlany obiektu obrazu. Ten element członkowski można wybrać jedno z następujących wartości:  
  
- **ILLUMINANT_EQUAL_ENERGY**  
  
- **ILLUMINANT_A**  
  
- **ILLUMINANT_B**  
  
- **ILLUMINANT_C**  
  
- **ILLUMINANT_D50**  
  
- **ILLUMINANT_D55**  
  
- **ILLUMINANT_D65**  
  
- **ILLUMINANT_D75**  
  
- **ILLUMINANT_F2**  
  
- **ILLUMINANT_TURNGSTEN**  
  
- **ILLUMINANT_DAYLIGHT**  
  
- **ILLUMINANT_FLUORESCENT**  
  
- **ILLUMINANT_NTSC**  
  
 *caRedGamma*  
 Określa wartość n-ty power korekcja gamma red podstawową kolorów źródła. Wartość musi należeć do zakresu od 2500 65 000. Wartość 10 000 oznacza nie korekcja gamma.  
  
 *caGreenGamma*  
 Określa wartość n-ty zasilania korekcja gamma zielony podstawową kolorów źródła. Wartość musi należeć do zakresu od 2500 65 000. Wartość 10 000 oznacza nie korekcja gamma.  
  
 *caBlueGamma*  
 Określa wartość n-ty zasilania korekcja gamma niebieski podstawową kolorów źródła. Wartość musi należeć do zakresu od 2500 65 000. Wartość 10 000 oznacza nie korekcja gamma.  
  
 *caReferenceBlack*  
 Określa czarny odwołanie kolorów źródła. Wszelkie kolorów, które są ciemniejsze od to są traktowane jako czarny. Wartość musi należeć do zakresu od 0 do 4000.  
  
 *caReferenceWhite*  
 Określa białe odwołanie kolorów źródła. Wszelkie kolorów, które są cieńszego niż to są traktowane jako biały. Wartość musi należeć do zakresu od 6000 do 10 000.  
  
 *caContrast*  
 Określa ilość kontrastu, mają być stosowane do obiektu źródłowego. Wartość musi należeć do zakresu od -100 do 100. Wartość 0 oznacza nie dopasowania kontrast.  
  
 *caBrightness*  
 Określa ilość jasności ma zostać zastosowany do obiektu źródłowego. Wartość musi należeć do zakresu od -100 do 100. Wartość 0 oznacza nie dopasowania Jasność.  
  
 *caColorfulness*  
 Określa ilość colorfulness ma zostać zastosowany do obiektu źródłowego. Wartość musi należeć do zakresu od -100 do 100. Wartość 0 oznacza nie dopasowania colorfulness.  
  
 *caRedGreenTint*  
 Określa ilość korekty odcień czerwone lub zielone ma zostać zastosowany do obiektu źródłowego. Wartość musi należeć do zakresu od -100 do 100. Dodatnie będzie dostosować do czerwony, a liczby ujemne Dostosuj kierunku zielony. Wartość 0 oznacza nie dopasowania odcień.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** wingdi.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetColorAdjustment](../../mfc/reference/cdc-class.md#getcoloradjustment)


