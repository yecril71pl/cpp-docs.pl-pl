---
title: Klasa CMFCImagePaintArea | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::GetMode
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetBitmap
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetColor
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetMode
dev_langs: C++
helpviewer_keywords:
- CMFCImagePaintArea [MFC], CMFCImagePaintArea
- CMFCImagePaintArea [MFC], GetMode
- CMFCImagePaintArea [MFC], SetBitmap
- CMFCImagePaintArea [MFC], SetColor
- CMFCImagePaintArea [MFC], SetMode
ms.assetid: c59eec22-f15a-4e58-8c4d-4a18a41f4452
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 70888bbd0acaef49bac67147bff4fe7719a84404
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cmfcimagepaintarea-class"></a>Klasa CMFCImagePaintArea
Udostępnia obszarze obrazu, który umożliwia modyfikowanie obrazu w oknie dialogowym edytora obrazów.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCImagePaintArea : public CButton  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|||  
|-|-|  
|Nazwa|Opis|  
|[CMFCImagePaintArea::CMFCImagePaintArea](#cmfcimagepaintarea)|Konstruuje `CMFCImagePaintArea` obiektu.|  
|`CMFCImagePaintArea::~CMFCImagePaintArea`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|||  
|-|-|  
|Nazwa|Opis|  
|[CMFCImagePaintArea::GetMode](#getmode)|Pobiera bieżący tryb rysowania.|  
|[CMFCImagePaintArea::SetBitmap](#setbitmap)|Ustawia obraz mapy bitowej dla obszaru obrazu.|  
|[CMFCImagePaintArea::SetColor](#setcolor)|Ustawia bieżący kolor rysowania.|  
|[CMFCImagePaintArea::SetMode](#setmode)|Ustawia bieżący tryb rysowania.|  
  
### <a name="remarks"></a>Uwagi  
 Ta klasa nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
 Aby wyświetlić obszar obrazu w oknie dialogowym edytora obrazów platformę korzysta z tej klasy. Aby uzyskać więcej informacji na temat okno dialogowe Edytor obrazu, zobacz [CMFCImageEditorDialog klasy](../../mfc/reference/cmfcimageeditordialog-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia obiektu `CMFCImagePaintArea` klasy, ustawienie bieżącej rysowania kolorów, ustawić bieżący tryb rysowania i ustawić obraz mapy bitowej dla obszaru obrazu.  
  
 [!code-cpp[NVC_MFC_RibbonApp#37](../../mfc/reference/codesnippet/cpp/cmfcimagepaintarea-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCImagePaintArea](../../mfc/reference/cmfcimagepaintarea-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afximagepaintarea.h  
  
##  <a name="cmfcimagepaintarea"></a>CMFCImagePaintArea::CMFCImagePaintArea  
 Konstruuje `CMFCImagePaintArea` obiektu.  
  
```  
CMFCImagePaintArea(CMFCImageEditorDialog* pParentDlg);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in]`pParentDlg`|Wskaźnik do okna dialogowego, który jest elementem nadrzędnym edytor obrazów.|  
  
##  <a name="getmode"></a>CMFCImagePaintArea::GetMode  
 Pobiera bieżący tryb rysowania.  
  
```  
IMAGE_EDIT_MODE GetMode() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 [IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md) wartość, która określa bieżący tryb rysowania.  
  
##  <a name="setbitmap"></a>CMFCImagePaintArea::SetBitmap  
 Ustawia obraz mapy bitowej dla obszaru obrazu.  
  
```  
void SetBitmap(CBitmap* pBitmap);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in]`pBitmap`|Nowy obraz mapy bitowej do wyświetlenia.|  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `pBitmap` jest `NULL`, ta metoda ustawia rozmiar obszaru można modyfikować paint równą zero. W przeciwnym razie ustawia rozmiar obszaru można modyfikować paint rozmiar obrazu dostarczonego mapy bitowej.  
  
##  <a name="setcolor"></a>CMFCImagePaintArea::SetColor  
 Ustawia bieżący kolor rysowania.  
  
```  
void SetColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in]`color`|Nowy kolor rysowania.|  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wybierz kolor na pasku palety edytora obrazów lub selektora kolorów, w ramach wywołuje tę metodę, aby zaktualizować bieżący kolor rysowania. Początkowy kolor rysowania jest czarny ( `COLORREF` wartość 0).  
  
 Kolor rysowania jest używany przez okno dialogowe Edytor obrazów dla wszystkie tryby rysowania z wyjątkiem `IMAGE_EDIT_MODE_COLOR`. Aby uzyskać więcej informacji na temat trybów rysowania, zobacz [wyliczenie CMFCImagePaintArea::IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md).  
  
##  <a name="setmode"></a>CMFCImagePaintArea::SetMode  
 Ustawia bieżący tryb rysowania.  
  
```  
void SetMode(IMAGE_EDIT_MODE mode);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in]`mode`|[IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md) wartość, która określa bieżący tryb rysowania.|  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md)
