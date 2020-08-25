---
title: Odwołanie kodowania ALT
ms.date: 11/04/2016
helpviewer_keywords:
- encoding
- encoding, functions
ms.assetid: 82d4fdf3-3c4a-4fe2-b297-8ffb4714406f
ms.openlocfilehash: a284645030b5bcdb30b72d7df92231680efb36b4
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831895"
---
# <a name="atl-encoding-reference"></a>Odwołanie kodowania ALT

Kodowanie w wielu typowych standardach internetowych, takich jak UUENCODE, szesnastkowe i UTF8, jest obsługiwane przez kod znaleziony w *`atlenc.h`* .

### <a name="functions"></a>Functions

| Funkcja | Przypadek użycia |
|--|--|
| [AtlGetHexValue](reference/atl-text-encoding-functions.md#atlgethexvalue) | Wywołaj tę funkcję, aby uzyskać wartość liczbową z liczby szesnastkowej. |
| [AtlHexDecode](reference/atl-text-encoding-functions.md#atlhexdecode) | Dekoduje ciąg danych, który został zakodowany jako tekst szesnastkowy, na przykład przez poprzednie wywołanie do [AtlHexEncode](reference/atl-text-encoding-functions.md#atlhexencode). |
| [AtlHexDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#atlhexdecodegetrequiredlength) | Wywołaj tę funkcję, aby uzyskać rozmiar (w bajtach) bufora, który może zawierać dane zdekodowane z ciągu zakodowanego szesnastkowo o określonej długości. |
| [AtlHexEncode](reference/atl-text-encoding-functions.md#atlhexencode) | Wywołaj tę funkcję, aby zakodować dane jako ciąg tekstu szesnastkowego. |
| [AtlHexEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#atlhexencodegetrequiredlength) | Wywołaj tę funkcję, aby uzyskać rozmiar (w znakach) bufora, który może zawierać ciąg zakodowany z danych o określonej długości. |
| [AtlUnicodeToUTF8](reference/atl-text-encoding-functions.md#atlunicodetoutf8) | Wywołaj tę funkcję, aby przekonwertować ciąg Unicode na UTF-8. |
| [BEncode](reference/atl-text-encoding-functions.md#bencode) | Wywołaj tę funkcję, aby skonwertować dane przy użyciu kodowania „B”. |
| [BEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#bencodegetrequiredlength) | Wywołaj tę funkcję, aby uzyskać rozmiar (w znakach) bufora, który może zawierać ciąg zakodowany z danych o określonej długości. |
| [EscapeXML](reference/atl-text-encoding-functions.md#escapexml) | Wywołaj tę funkcję, aby skonwertować znaki niebezpieczne w XML na ich bezpieczne odpowiedniki. |
| [GetExtendedChars](reference/atl-text-encoding-functions.md#getextendedchars) | Wywołaj tę funkcję, aby uzyskać liczbę znaków rozszerzonych w ciągu. |
| [IsExtendedChar](reference/atl-text-encoding-functions.md#isextendedchar) | Wywołaj tę funkcję, aby dowiedzieć się, czy dany znak jest znakiem rozszerzonym (mniejszym niż 32, większym niż 126, a nie tabulatorem, znakiem wysuwu wiersza ani returnem) |
| [QEncode](reference/atl-text-encoding-functions.md#qencode) | Wywołaj tę funkcję, aby skonwertować dane przy użyciu kodowania „Q”. |
| [QEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#qencodegetrequiredlength) | Wywołaj tę funkcję, aby uzyskać rozmiar (w znakach) bufora, który może zawierać ciąg zakodowany z danych o określonej długości. |
| [QPDecode](reference/atl-text-encoding-functions.md#qpdecode) | Dekoduje ciąg danych, który został zakodowany w formacie do drukowania w cudzysłowie, na przykład przez poprzednie wywołanie do [QPEncode](reference/atl-text-encoding-functions.md#qpencode). |
| [QPDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#qpdecodegetrequiredlength) | Wywołaj tę funkcję, aby uzyskać rozmiar (w bajtach) bufora, który może zawierać dane zdekodowane z ciągu zakodowanego w quoted-printable o określonej długości. |
| [QPEncode](reference/atl-text-encoding-functions.md#qpencode) | Wywołaj tę funkcję, aby zakodować dane w formacie quoted-printable. |
| [QPEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#qpencodegetrequiredlength) | Wywołaj tę funkcję, aby uzyskać rozmiar (w znakach) bufora, który może zawierać ciąg zakodowany z danych o określonej długości. |
| [UUDecode](reference/atl-text-encoding-functions.md#uudecode) | Dekoduje ciąg danych, który został wystawiony na przykład przez poprzednie wywołanie do [UUENCODE](reference/atl-text-encoding-functions.md#uuencode). |
| [UUDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#uudecodegetrequiredlength) | Wywołaj tę funkcję, aby uzyskać rozmiar (w bajtach) bufora, który może zawierać dane zdekodowane z ciągu zakodowanego w uuencode o określonej długości. |
| [UUEncode](reference/atl-text-encoding-functions.md#uuencode) | Wywołaj tę funkcję, aby zakodować dane w uuencode. |
| [UUEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#uuencodegetrequiredlength) | Wywołaj tę funkcję, aby uzyskać rozmiar (w znakach) bufora, który może zawierać ciąg zakodowany z danych o określonej długości. |

## <a name="see-also"></a>Zobacz też

[Pojęcia](../atl/active-template-library-atl-concepts.md)<br/>
[Składniki pulpitu COM ATL](../atl/atl-com-desktop-components.md)
