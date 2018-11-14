---
title: Struktura BITMAP
ms.date: 11/04/2016
f1_keywords:
- BITMAP
helpviewer_keywords:
- BITMAP structure [MFC]
ms.assetid: 05d33b4d-7232-4643-a108-87dda8ff5f22
ms.openlocfilehash: a9ffa7191b5f0e815db9c7e8b8a26b0b6b200f2d
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330245"
---
# <a name="bitmap-structure"></a>Struktura BITMAP

**Mapy BITOWEJ** definiuje strukturę, wysokość, szerokość, format koloru i wartości bitowe logicznej mapy bitowej.

## <a name="syntax"></a>Składnia

```
typedef struct tagBITMAP {  /* bm */
    int bmType;
    int bmWidth;
    int bmHeight;
    int bmWidthBytes;
    BYTE bmPlanes;
    BYTE bmBitsPixel;
    LPVOID bmBits;
} BITMAP;
```

#### <a name="parameters"></a>Parametry

*bmType*<br/>
Określa typ mapy bitowej. W przypadku logicznych map bitowych ten element członkowski musi mieć wartość 0.

*bmWidth*<br/>
Określa szerokość mapy bitowej w pikselach. Szerokość musi być większa od 0.

*bmHeight*<br/>
Określa wysokość mapy bitowej w wierszach rastrowych. Wysokość musi być większa od 0.

*bmWidthBytes*<br/>
Określa liczbę bajtów w każdym wierszu rastrowym. Ta wartość musi być liczbą parzystą, ponieważ graficzny interfejs urządzenia (GDI) zakłada, że wartości bitowe mapy bitowej tworzą tablicę wartości całkowitych (2-bajtowych). Innymi słowy *bmWidthBytes* \* 8 musi być kolejną wielokrotnością liczby 16, większą lub równą wartości uzyskanej po *bmWidth* elementu członkowskiego jest mnożony przez *bmBitsPixel*  elementu członkowskiego.

*bmPlanes*<br/>
Określa liczbę płaszczyzn kolorów w mapie bitowej.

*bmBitsPixel*<br/>
Określa liczbę bitów sąsiadujących kolorów na każdej płaszczyźnie niezbędnej do zdefiniowania piksela.

*bmBits*<br/>
Wskazuje lokalizację wartości bitowych mapy bitowej. *BmBits* elementu członkowskiego musi być wskaźnikiem long do tablicy wartości 1-bajtowe.

## <a name="remarks"></a>Uwagi

Obecnie są stosowane dwa formaty map bitowych: monochromatyczne i kolorowe. Mapa bitowa monochromatyczna używa formatu 1-bitowego 1-płaszczyznowego. Każde skanowanie jest wielokrotnością 16 bitów.

Skanowania są zorganizowane w następujący sposób dla monochromatycznych map bitowych o wysokości *n*:

```
Scan 0
Scan 1
.
.
.
Scan n-2
Scan n-1
```

Piksele na urządzeniu monochromatycznym są czarne lub białe. Jeśli odnośny bit w mapie bitowej ma wartość 1, piksel jest włączony (biały). Gdy odnośny bit w mapie bitowej ma wartość 0, piksel jest wyłączony (czarny).

Wszystkie urządzenia obsługują mapy bitowe, które mają zestaw rastercaps bit w indeksie RASTERCAPS [rc_bitblt](../../mfc/reference/cdc-class.md#getdevicecaps) funkcja elementu członkowskiego.

Każde urządzenie ma własny unikatowy format koloru. W celu przekazania bitmapy z jednego urządzenia do innego, należy użyć [GetDIBits](/windows/desktop/api/wingdi/nf-wingdi-getdibits) i [SetDIBits](/windows/desktop/api/wingdi/nf-wingdi-setdibits) funkcje Windows.

## <a name="requirements"></a>Wymagania

**Nagłówek:** wingdi.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect)
