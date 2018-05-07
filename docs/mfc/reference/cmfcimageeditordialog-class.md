---
title: Klasa CMFCImageEditorDialog | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog::CMFCImageEditorDialog
dev_langs:
- C++
helpviewer_keywords:
- CMFCImageEditorDialog [MFC], CMFCImageEditorDialog
ms.assetid: 6a7d08f3-1ec2-4062-9b79-a0c2776b58d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 795e5548e93323af389c3faeaefa7dda0bf7d80c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcimageeditordialog-class"></a>Klasa CMFCImageEditorDialog
`CMFCImageEditorDialog` Klasa obsługuje okno dialogowe Edytor obrazu.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCImageEditorDialog : public CDialogEx  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCImageEditorDialog::CMFCImageEditorDialog](#cmfcimageeditordialog)|Konstruuje `CMFCImageEditorDialog` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 `CMFCImageEditorDialog` Klasa udostępnia okno dialogowe, które obejmują:  
  
-   Obszar obrazu, który umożliwia modyfikowanie piksele obrazu.  
  
-   Rysowanie narzędzi, aby zmodyfikować pikseli w obszarze obrazu.  
  
-   Palety kolorów, aby określić kolor, który jest używany przez narzędzia do rysowania.  
  
-   Obszar podglądu, który wyświetla efekt edycji.  
  
 Na poniższej ilustracji przedstawiono edytor obrazów — okno dialogowe.  
  
 ![Okno dialogowe CMFCImageEditorDialog](../../mfc/reference/media/imageedit.png "imageedit")  
  
 Aby użyć `CMFCImageEditorDialog` obiekt jest przekazywany `CBitmap` obraz, który można edytować. Nie należy tworzyć duży obraz, ponieważ rozmiar ograniczone jest edytowania obszaru obrazu, a rozmiar logiczny pikseli zostanie dopasowana do obszaru. Wywołanie `DoModal` metodę, aby uruchomić modalne okno dialogowe.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afximageeditordialog.h  
  
##  <a name="cmfcimageeditordialog"></a>  CMFCImageEditorDialog::CMFCImageEditorDialog  
 Konstruuje `CMFCImageEditorDialog` obiektu.  
  
```  
CMFCImageEditorDialog(
    CBitmap* pBitmap,  
    CWnd* pParent=NULL,  
    int nBitsPixel=-1);
```  
  
### <a name="parameters"></a>Parametry  
 `pBitmap`  
 Wskaźnik do obrazu.  
  
 `pParent`  
 Wskaźnik do okna nadrzędnego bieżące okno dialogowe Edytor obrazu.  
  
 `nBitsPixel`  
 Liczba bitów używany do reprezentowania kolor piksela, który jest również określana jako głębi kolorów.  Jeśli `nBitsPixel` parametru wynosi -1, głębi kolorów jest określana na podstawie określonego przez obrazu `pBitmap` parametru. Wartość domyślna wynosi -1.  
  
### <a name="return-value"></a>Wartość zwracana  
 Aby zmodyfikować obraz, wskaźnikiem obrazu do `CMFCImageEditorDialog` konstruktora. Następnie wywołaj `DoModal` metodę, aby otworzyć modalne okno dialogowe. Gdy `DoModal` metoda zwróci wartość, mapy bitowej zawiera nowy obraz.  
  
### <a name="remarks"></a>Uwagi  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia obiektu `CMFCImageEditorDialog` klasy. Ten przykład jest częścią [próbki nowe formanty](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#8](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_1.cpp)]  
[!code-cpp[NVC_MFC_NewControls#40](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_2.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)
