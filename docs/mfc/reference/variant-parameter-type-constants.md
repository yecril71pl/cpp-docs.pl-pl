---
title: Stałe typów parametru Variant | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 13820ff4fb07c3743f36ba3ebe33ee56a3a79c7d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379863"
---
# <a name="variant-parameter-type-constants"></a>Stałe typów parametru Variant
W tym temacie wymieniono nowe stałe, które wskazują typów parametru variant przeznaczony do użytku z klasy formantów OLE programu Microsoft Foundation Class Library.  
  
 Poniżej przedstawiono listę stałe klasy:  
  
##  <a name="_mfc_variant_data_constants"></a> Variant — stałe danych  
  
-   **Vts_color —** A 32-bitowa liczba całkowita, używany do reprezentowania wartości kolorów RGB.  
  
-   **Vts_font —** wskaźnik do **IFontDisp** interfejsu obiektu czcionki.  
  
-   **Vts_handle —** wartość obsługi systemu Windows.  
  
-   **Vts_picture —** wskaźnik do `IPictureDisp` interfejsu obiektu obrazu.  
  
-   **Vts_optexclusive —** A 16-bitową wartość używany dla formantu, który jest przeznaczony do użycia w grupie formanty, takie jak przyciski radiowe. Ten typ Określa, że kontenera czy jeśli jedne kontrolować w grupie ma **TRUE** wartości wszystkich innych atrybutów muszą być **FALSE**.  
  
-   **Vts_tristate —** A 16-bitową liczbę całkowitą ze znakiem używane dla właściwości, które mogą mieć jeden z trzech wartości (wybrane, wyczyszczone, niedostępny), na przykład pole wyboru.  
  
-   **Vts_xpos_himetric —** używany do reprezentowania położenie wzdłuż osi x liczbę całkowitą bez znaku A 32-bitowych **HIMETRIC** jednostki.  
  
-   **Vts_ypos_himetric —** używany do reprezentowania położenie wzdłuż osi y w liczbę całkowitą bez znaku A 32-bitowych **HIMETRIC** jednostki.  
  
-   **Vts_xpos_pixels —** używany do reprezentowania położenie na osi x w pikselach liczbę całkowitą bez znaku A 32-bitowych.  
  
-   **Vts_ypos_pixels —** używany do reprezentowania położenie wzdłuż osi y w pikselach liczbę całkowitą bez znaku A 32-bitowych.  
  
-   **Vts_xsize_pixels —** używany do reprezentowania szerokość obiektu ekranu w pikselach liczbę całkowitą bez znaku A 32-bitowych.  
  
-   **Vts_ysize_pixels —** używany do reprezentowania wysokość obiektu ekranu w pikselach liczbę całkowitą bez znaku A 32-bitowych.  
  
-   **Vts_xsize_himetric —** używany do reprezentowania szerokość obiektu ekranu na liczbę całkowitą bez znaku A 32-bitowych **HIMETRIC** jednostki.  
  
-   **Vts_ysize_himetric —** używany do reprezentowania wysokość obiektu ekranu na liczbę całkowitą bez znaku A 32-bitowych **HIMETRIC** jednostki.  
  
    > [!NOTE]
    >  Dodatkowe stałe variant zostały zdefiniowane dla wszystkich typów variant, z wyjątkiem produktów **vts_font —** i **vts_picture —**, które zapewniają wskaźnik co danych variant nstant. Stałe te są nazywane przy użyciu **VTS_P** `constantname` Konwencji. Na przykład **VTS_PCOLOR** jest wskaźnikiem do **vts_color —** stałej.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdisp.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
