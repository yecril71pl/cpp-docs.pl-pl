---
title: Struktura BITMAPINFO | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- BITMAPINFO
dev_langs:
- C++
helpviewer_keywords:
- BITMAPINFO structure [MFC]
ms.assetid: a00caa49-e4df-419f-89a7-ab03c13a1b5b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9e114af97385241674cf9baa4f8d9883acdadef3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405960"
---
# <a name="bitmapinfo-structure"></a>Struktura BITMAPINFO

`BITMAPINFO` Definiuje strukturę, wymiary i informacji o kolorze do mapy bitowej Windows niezależnych od urządzenia (DIB).

## <a name="syntax"></a>Składnia

```
typedef struct tagBITMAPINFO {
    BITMAPINFOHEADER bmiHeader;
    RGBQUAD bmiColors[1];
} BITMAPINFO;
```

#### <a name="parameters"></a>Parametry

*bmiHeader*<br/>
Określa [BITMAPINFOHEADER](https://msdn.microsoft.com/library/windows/desktop/dd183376) strukturę, która zawiera informacje dotyczące wymiarów i format koloru z mapy bitowej niezależnych od urządzenia.

*bmiColors*<br/>
Określa tablicę [RGBQUAD](/windows/desktop/api/wingdi/ns-wingdi-tagrgbquad) lub DWORD typów danych, które definiują kolorów w mapie bitowej.

## <a name="remarks"></a>Uwagi

Mapy bitowej niezależnych od urządzenia składa się z dwóch części: `BITMAPINFO` strukturę, która w tym artykule opisano wymiary i kolorów mapy bitowej i tablicę bajtów, które określają pikseli w mapie bitowej. Usługa bits w tablicy są pakowane razem, ale każdy wiersz skanowania musi dopełniana zerami w celu zakończenia na **długie** granic. Gdy wysokość jest dodatnia, mapy bitowej pochodzi z lewego dolnego rogu. Gdy wysokość jest ujemna, pochodzi lewego górnego rogu.

A *upakowaną mapy bitowej* jest mapą bitową, gdzie następuje tablicy bajtowej `BITMAPINFO` struktury. Mapy bitowe upakowaną odwołują się jednego wskaźnika.

Aby uzyskać więcej informacji na temat `BITMAPINFO` struktury i odpowiednie wartości dla elementów członkowskich `BITMAPINFOHEADER` i `RGBQUAD` struktur, zobacz następujące tematy w dokumentacji zestawu Windows SDK.

- [Struktura BITMAPINFO](/windows/desktop/api/wingdi/ns-wingdi-tagbitmapinfo)

- [BITMAPINFOHEADER](https://msdn.microsoft.com/library/windows/desktop/dd183376) struktury

- [RGBQUAD](/windows/desktop/api/wingdi/ns-wingdi-tagrgbquad) struktury

## <a name="requirements"></a>Wymagania

**Nagłówek:** wingdi.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CBrush::CreateDIBPatternBrush](../../mfc/reference/cbrush-class.md#createdibpatternbrush)<br/>
[BITMAPINFOHEADER](https://msdn.microsoft.com/library/windows/desktop/dd183376)<br/>
[RGBQUAD](/windows/desktop/api/wingdi/ns-wingdi-tagrgbquad)

