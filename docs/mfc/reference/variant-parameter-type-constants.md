---
title: Stałe typów parametru Variant
ms.date: 11/04/2016
f1_keywords:
- VTS_YPOS_HIMETRIC
- VTS_PICTURE
- VTS_FONT
- VTS_XPOS_HIMETRIC
- VTS_XPOS_PIXELS
- VTS_XSIZE_HIMETRIC
- VTS_YPOS_PIXELS
- VTS_TRISTATE
- VTS_HANDLE
- VTS_YSIZE_HIMETRIC
- VTS_COLOR
- VTS_OPTEXCLUSIVE
- VTS_YSIZE_PIXELS
- VTS_XSIZE_PIXELS
helpviewer_keywords:
- VTS_XPOS_HIMETRIC constant [MFC]
- VTS_FONT constant [MFC]
- VTS_XPOS_PIXELS constant [MFC]
- VTS_COLOR constant [MFC]
- Variants [MFC]
- VTS_YPOS_PIXELS constant [MFC]
- VTS_YSIZE_HIMETRIC constant [MFC]
- VTS_YPOS_HIMETRIC constant [MFC]
- Variants, parameter type constants
- Variant data constants [MFC]
- VTS_PICTURE constant [MFC]
- VTS_TRISTATE constant [MFC]
- VTS_XSIZE_HIMETRIC constant [MFC]
- VTS_HANDLE constant [MFC]
- VTS_XSIZE_PIXELS constant [MFC]
- VTS_OPTEXCLUSIVE constant [MFC]
- VTS_YSIZE_PIXELS constant [MFC]
ms.assetid: de99c7a9-7aae-4dc4-b723-40c6380543ab
ms.openlocfilehash: b15a303f69ce13cf3ba3b6c1c0739acdb8a33c7c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62309483"
---
# <a name="variant-parameter-type-constants"></a>Stałe typów parametru Variant

W tym temacie opisano nowe stałe, które wskazują typów parametru variant przeznaczony do użytku z klasy formantów OLE z biblioteki klas Microsoft Foundation.

Poniżej przedstawiono listę stałych, klas:

##  <a name="_mfc_variant_data_constants"></a> Variant — stałe danych

- VTS_COLOR 32-bitowa liczba całkowita, używany do reprezentowania wartości kolorów RGB.

- Wskaźnik A VTS_FONT `IFontDisp` interfejs obiektu czcionki.

- Wartość dojścia VTS_HANDLE Windows.

- Wskaźnik A VTS_PICTURE `IPictureDisp` interfejs obiektu obrazu.

- VTS_OPTEXCLUSIVE 16-bitową wartość dla formantu, który jest przeznaczony do użycia w grupie formanty, takie jak przyciski radiowe. Ten typ informuje kontener, jeśli jeden formant w grupie ma wartość TRUE, wszystkie inne musi być równa FALSE.

- VTS_TRISTATE 16-bitowa liczba całkowita używane dla właściwości, które mogą mieć jeden z trzech wartości (wybrane, wyczyszczone, niedostępny), na przykład pole wyboru.

- VTS_XPOS_HIMETRIC 32-bitowa liczba całkowita bez znaku używany do reprezentowania pozycja wzdłuż osi x w jednostkach HIMETRIC.

- VTS_YPOS_HIMETRIC 32-bitowa liczba całkowita bez znaku używany do reprezentowania pozycja wzdłuż osi y w jednostkach HIMETRIC.

- VTS_XPOS_PIXELS 32-bitowa liczba całkowita bez znaku używany do reprezentowania pozycja wzdłuż osi x w pikselach.

- VTS_YPOS_PIXELS 32-bitowa liczba całkowita bez znaku używany do reprezentowania pozycja wzdłuż osi y w pikselach.

- VTS_XSIZE_PIXELS 32-bitowa liczba całkowita bez znaku używany do reprezentowania szerokość ekranu obiektu w pikselach.

- VTS_YSIZE_PIXELS 32-bitowa liczba całkowita bez znaku używany do reprezentowania wysokość obiekt ekranu w pikselach.

- VTS_XSIZE_HIMETRIC 32-bitowa liczba całkowita bez znaku używany do reprezentowania szerokość ekranu obiektu w jednostkach HIMETRIC.

- VTS_YSIZE_HIMETRIC 32-bitowa liczba całkowita bez znaku używany do reprezentowania wysokość obiekt ekranu w jednostkach HIMETRIC.

    > [!NOTE]
    >  Dodatkowe variant — stałe zostały zdefiniowane dla wszystkich wariantów typów, z wyjątkiem VTS_FONT i VTS_PICTURE, stanowiące wskaźnik ze stałą danych variant. Te stałe są nazywane przy użyciu VTS_P`constantname` Konwencji. Na przykład VTS_PCOLOR jest wskaźnikiem do VTS_COLOR — stała.

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="see-also"></a>Zobacz także

[Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
