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
ms.openlocfilehash: f73c72830216679f8a91d0037d48c1e1b8e400c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372866"
---
# <a name="variant-parameter-type-constants"></a>Stałe typów parametru Variant

W tym temacie wymieniono nowe stałe, które wskazują typy parametrów wariantu przeznaczone do użycia z klasami sterowania OLE biblioteki klas Programu Microsoft Foundation.

Poniżej znajduje się lista stałych klas:

## <a name="variant-data-constants"></a><a name="_mfc_variant_data_constants"></a>Stałe danych wariantowych

- VTS_COLOR 32-bitowa całkowitej liczby używanej do reprezentowania wartości koloru RGB.

- VTS_FONT Wskaźnik do `IFontDisp` interfejsu obiektu czcionek OLE.

- VTS_HANDLE wartość uchwytu systemu Windows.

- VTS_PICTURE Wskaźnik do `IPictureDisp` interfejsu obiektu obrazu OLE.

- VTS_OPTEXCLUSIVE Wartość 16-bitowa używana dla formantu, który ma być używany w grupie formantów, takich jak przyciski radiowe. Ten typ informuje kontenera, że jeśli jeden formant w grupie ma wartość PRAWDA, wszystkie inne muszą być FALSE.

- VTS_TRISTATE 16-bitowa liczba całkowita z podpisem używanym dla właściwości, które mogą mieć jedną z trzech możliwych wartości (zaznaczone, wyczyszczone, niedostępne), na przykład pole wyboru.

- VTS_XPOS_HIMETRIC 32-bitowa niepodpisana liczba całkowita używana do reprezentowania pozycji wzdłuż osi x w jednostkach HIMETRIC.

- VTS_YPOS_HIMETRIC 32-bitową niepodpisaną całkowitej liczby użytej do reprezentowania pozycji wzdłuż osi y w jednostkach HIMETRIC.

- VTS_XPOS_PIXELS 32-bitowa niepodpisana liczba całkowita używana do reprezentowania pozycji wzdłuż osi x w pikselach.

- VTS_YPOS_PIXELS 32-bitowa niepodpisana liczba całkowita używana do reprezentowania pozycji wzdłuż osi y w pikselach.

- VTS_XSIZE_PIXELS 32-bitowa niepodpisana liczba całkowita używana do reprezentowania szerokości obiektu ekranu w pikselach.

- VTS_YSIZE_PIXELS 32-bitowa niepodpisana liczba całkowita używana do reprezentowania wysokości obiektu ekranu w pikselach.

- VTS_XSIZE_HIMETRIC 32-bitowa niepodpisana liczba całkowita używana do reprezentowania szerokości obiektu ekranu w jednostkach HIMETRIC.

- VTS_YSIZE_HIMETRIC 32-bitowa niepodpisana liczba całkowita używana do reprezentowania wysokości obiektu ekranu w jednostkach HIMETRIC.

    > [!NOTE]
    >  Dodatkowe stałe wariantu zostały zdefiniowane dla wszystkich typów wariantów, z wyjątkiem VTS_FONT i VTS_PICTURE, które zapewniają wskaźnik do stałej danych wariantu. Te stałe są nazwane przy`constantname` użyciu konwencji VTS_P. Na przykład VTS_PCOLOR jest wskaźnikiem do stałej VTS_COLOR.

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="see-also"></a>Zobacz też

[Makra i globals](../../mfc/reference/mfc-macros-and-globals.md)
