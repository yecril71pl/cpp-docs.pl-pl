---
title: Klasa CMFCRibbonButtonsGroup | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::AddButton
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::AddButtons
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetButton
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetCount
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetImageSize
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetRegularSize
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::HasImages
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::OnDrawImage
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::RemoveAll
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::SetImages
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::SetParentCategory
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonButtonsGroup [MFC], CMFCRibbonButtonsGroup
- CMFCRibbonButtonsGroup [MFC], AddButton
- CMFCRibbonButtonsGroup [MFC], AddButtons
- CMFCRibbonButtonsGroup [MFC], GetButton
- CMFCRibbonButtonsGroup [MFC], GetCount
- CMFCRibbonButtonsGroup [MFC], GetImageSize
- CMFCRibbonButtonsGroup [MFC], GetRegularSize
- CMFCRibbonButtonsGroup [MFC], HasImages
- CMFCRibbonButtonsGroup [MFC], OnDrawImage
- CMFCRibbonButtonsGroup [MFC], RemoveAll
- CMFCRibbonButtonsGroup [MFC], SetImages
- CMFCRibbonButtonsGroup [MFC], SetParentCategory
ms.assetid: b993d93e-fc1a-472f-a87f-1d7b7b499845
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 855bc48da10e8ca4dd83cf091e155746450a33f1
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848522"
---
# <a name="cmfcribbonbuttonsgroup-class"></a>Klasa CMFCRibbonButtonsGroup
`CMFCRibbonButtonsGroup` Klasa umożliwia organizowanie zestawu przycisków wstążki w grupę. Wszystkie przyciski w grupie są bezpośrednio przylegające do siebie w poziomie i ujęte w obramowaniu.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCRibbonButtonsGroup : public CMFCRibbonBaseElement  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup](#cmfcribbonbuttonsgroup)|Konstruuje `CMFCRibbonButtonsGroup` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCRibbonButtonsGroup::AddButton](#addbutton)|Dodaje przycisk do grupy.|  
|[CMFCRibbonButtonsGroup::AddButtons](#addbuttons)|Dodaje listę przycisków do grupy.|  
|[CMFCRibbonButtonsGroup::GetButton](#getbutton)|Zwraca wskaźnik do przycisku, który jest umieszczony pod określonym indeksem.|  
|[CMFCRibbonButtonsGroup::GetCount](#getcount)|Zwraca liczbę przycisków w grupie.|  
|[CMFCRibbonButtonsGroup::GetImageSize](#getimagesize)|Zwraca rozmiar obrazu normalne obrazów w grupy wstążki (zastępuje [CMFCRibbonBaseElement::GetImageSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getimagesize).)|  
|[CMFCRibbonButtonsGroup::GetRegularSize](#getregularsize)|Zwraca zwykłego rozmiaru elementu wstążki (zastępuje [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|  
|[CMFCRibbonButtonsGroup::HasImages](#hasimages)|Raporty czy `CMFCRibbonButtonsGroup` obiekt zawiera obrazy paska narzędzi.|  
|[CMFCRibbonButtonsGroup::OnDrawImage](#ondrawimage)|Rysuje odpowiedni obraz dla określonego przycisku, w zależności od tego, czy przycisk jest normalna, wyróżnione lub wyłączone.|  
|[CMFCRibbonButtonsGroup::RemoveAll](#removeall)|Usuwa wszystkie przyciski z `CMFCRibbonButtonsGroup` obiektu.|  
|[CMFCRibbonButtonsGroup::SetImages](#setimages)|Obrazy są przypisywane do grupy.|  
|[CMFCRibbonButtonsGroup::SetParentCategory](#setparentcategory)|Ustawia element nadrzędny `CMFCRibbonCategory` z `CMFCRibbonButtonsGroup` obiekt i wszystkie przyciski w nim (zastępuje [CMFCRibbonBaseElement::SetParentCategory](../../mfc/reference/cmfcribbonbaseelement-class.md#setparentcategory).)|  
  
## <a name="remarks"></a>Uwagi  
 Grupy jest tworzony na podstawie [CMFCBaseRibbonElement](../../mfc/reference/cmfcribbonbaseelement-class.md) i mogą być zmieniane jako pojedynczy element. Grupy można umieścić w dowolnym panel lub menu podręcznego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak korzystać z różnych metod w `CMFCRibbonButtonsGroup` klasy. W przykładzie pokazano sposób tworzenia `CMFCRibbonButtonsGroup` obiektu, przypisywanie obrazów do grupy przycisków Wstążki i dodać przycisk do grupy przycisków wstążki. Ten fragment kodu jest częścią [Rysowanie Client sample](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DrawClient#2](../../mfc/reference/codesnippet/cpp/cmfcribbonbuttonsgroup-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButtonsGroup](../../mfc/reference/cmfcribbonbuttonsgroup-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxribbonbuttonsgroup.h  
  
##  <a name="addbutton"></a>  CMFCRibbonButtonsGroup::AddButton  
 Dodaje przycisk do grupy.  
  
```  
void AddButton(CMFCRibbonBaseElement* pButton);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pButton*  
 Wskaźnik do przycisku, aby dodać.  
  
##  <a name="addbuttons"></a>  CMFCRibbonButtonsGroup::AddButtons  
 Dodaje listę przycisków do grupy.  
  
```  
void AddButtons(
    const CList<CMFCRibbonBaseElement*,CMFCRibbonBaseElement*>& lstButtons);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *lstButtons*  
 Lista wskaźników do przycisków, które chcesz dodać.  
  
##  <a name="cmfcribbonbuttonsgroup"></a>  CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup  
 Konstruuje `CMFCRibbonButtonsGroup` obiektu.  
  
```  
CMFCRibbonButtonsGroup();
CMFCRibbonButtonsGroup(CMFCRibbonBaseElement* pButton);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pButton*  
 Określa przycisk, aby dodać do nowo utworzonego `CMFCRibbonButtonsGroup` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getbutton"></a>  CMFCRibbonButtonsGroup::GetButton  
 Zwraca wskaźnik do przycisku, który jest umieszczony pod określonym indeksem.  
  
```  
CMFCRibbonBaseElement* GetButton(int i) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *i*  
 Liczony od zera indeks przycisk, aby wrócić.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do przycisku, który jest umieszczony pod określonym indeksem. Wartość NULL, jeśli określony indeks jest poza zakresem.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getcount"></a>  CMFCRibbonButtonsGroup::GetCount  
 Zwraca liczbę przycisków w grupie.  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba przycisków w grupie.  
  
##  <a name="getimagesize"></a>  CMFCRibbonButtonsGroup::GetImageSize  
 Pobiera rozmiar obrazu źródłowego chronionych `CMFCToolBarImages` elementu członkowskiego `m_Images`.  
  
```  
const CSize GetImageSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca rozmiar obrazu źródłowego paska narzędzi obrazów, jeśli są obecne, a `CSize` o wartości zero, jeśli nie.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getregularsize"></a>  CMFCRibbonButtonsGroup::GetRegularSize  
 Pobiera maksymalny rozmiar elementu grupy wstążki.  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *podstawowego kontrolera domeny*  
 Wskaźnik do kontekstu urządzenia z grupy wstążki.  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="hasimages"></a>  CMFCRibbonButtonsGroup::HasImages  
 Raporty czy `CMFCRibbonButtonsGroup` obiekt zawiera obrazy paska narzędzi.  
  
```  
BOOL HasImages() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli chronionego `CMFCToolBarImages` elementu członkowskiego `m_Images` nie zawiera żadnych obrazów lub, jeśli wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="ondrawimage"></a>  CMFCRibbonButtonsGroup::OnDrawImage  
 Rysuje odpowiedni obraz dla określonego przycisku, w zależności od tego, czy przycisk jest normalna, wyróżnione lub wyłączone.  
  
```  
virtual void OnDrawImage(
    CDC* pDC,  
    CRect rectImage,  
    CMFCRibbonBaseElement* pButton,  
    int nImageIndex);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *podstawowego kontrolera domeny*  
 Wskaźnik do kontekstu urządzenia `CMFCRibbonButtonsGroup` obiektu.  
  
 [in] *rectImage*  
 Prostokąt, w którym do rysowania obrazu.  
  
 [in] *pButton*  
 Przycisk do rysowania obrazu.  
  
 [in] *nImageIndex*  
 Indeks obrazu, aby rysować na przycisku (w jednym z tablic obraz trzech przycisków normalne, wyróżnione lub wyłączone).  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="removeall"></a>  CMFCRibbonButtonsGroup::RemoveAll  
 Usuwa wszystkie przyciski z `CMFCRibbonButtonsGroup` obiektu.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setimages"></a>  CMFCRibbonButtonsGroup::SetImages  
 Obrazy są przypisywane do grupy przycisków wstążki.  
  
```  
void SetImages(
    CMFCToolBarImages* pImages,  
    CMFCToolBarImages* pHotImages,  
    CMFCToolBarImages* pDisabledImages);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pImages*  
 Zwykłych obrazów.  
  
 [in] *pHotImages*  
 Wymiennymi obrazami.  
  
 [in] *pDisabledImages*  
 Obrazy wyłączone.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj `SetImages` przed dodaniem przycisków do grupy. Liczba obrazów musi być większa lub równa liczbie przycisków, które mają zostać dodane do grupy.  
  
> [!NOTE]
>  Wymiennymi obrazami są obrazy, które są wyświetlane, gdy użytkownik zatrzyma na przycisku. Wyłączone obrazy są obrazy, które są wyświetlane, gdy przycisk został wyłączony.  
  
##  <a name="setparentcategory"></a>  CMFCRibbonButtonsGroup::SetParentCategory  
 Ustawia element nadrzędny `CMFCRibbonCategory` z `CMFCRibbonButtonsGroup` obiekt i wszystkie przyciski w nim.  
  
```  
virtual void SetParentCategory(CMFCRibbonCategory* pCategory);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pCategory*  
 Wskaźnik do kategorii nadrzędnej, aby ustawić (grupy z kartami w formanty wstążki są nazywane kategorii).  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)
