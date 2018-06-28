---
title: Klasa CMFCRibbonSlider | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider::CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetPos
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRangeMax
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRangeMin
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRegularSize
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetZoomIncrement
- AFXRIBBONSLIDER/CMFCRibbonSlider::HasZoomButtons
- AFXRIBBONSLIDER/CMFCRibbonSlider::OnDraw
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetPos
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetRange
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetZoomButtons
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetZoomIncrement
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonSlider [MFC], CMFCRibbonSlider
- CMFCRibbonSlider [MFC], GetPos
- CMFCRibbonSlider [MFC], GetRangeMax
- CMFCRibbonSlider [MFC], GetRangeMin
- CMFCRibbonSlider [MFC], GetRegularSize
- CMFCRibbonSlider [MFC], GetZoomIncrement
- CMFCRibbonSlider [MFC], HasZoomButtons
- CMFCRibbonSlider [MFC], OnDraw
- CMFCRibbonSlider [MFC], SetPos
- CMFCRibbonSlider [MFC], SetRange
- CMFCRibbonSlider [MFC], SetZoomButtons
- CMFCRibbonSlider [MFC], SetZoomIncrement
ms.assetid: 9351ac34-f234-4e42-91e2-763f1989c8ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 06575c4d014f72ddbae63ea5f02c3081b4228e1d
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37037732"
---
# <a name="cmfcribbonslider-class"></a>Klasa CMFCRibbonSlider
`CMFCRibbonSlider` Klasa implementuje formant suwaka, który można dodać do pasek Wstążki lub pasek stanu wstążki. Kontrolka suwaka wstążki podobny suwaki powiększenia, które są widoczne w aplikacjach pakietu Office 2007.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCRibbonSlider : public CMFCRibbonBaseElement  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCRibbonSlider::CMFCRibbonSlider](#cmfcribbonslider)|Tworzy i inicjuje formantu suwaka wstążki.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCRibbonSlider::GetPos](#getpos)|Zwraca bieżące położenie suwaka.|  
|[CMFCRibbonSlider::GetRangeMax](#getrangemax)|Zwraca maksymalną wartość suwaka.|  
|[CMFCRibbonSlider::GetRangeMin](#getrangemin)|Zwraca minimalną wartość suwaka.|  
|[CMFCRibbonSlider::GetRegularSize](#getregularsize)|Zwraca zwykłego rozmiaru elementu wstążki. (Przesłania [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|  
|[CMFCRibbonSlider::GetZoomIncrement](#getzoomincrement)|Zwraca rozmiar zmiany wielkości dla kontrolki suwaka.|  
|[CMFCRibbonSlider::HasZoomButtons](#haszoombuttons)|Określa, czy suwak ma przycisków powiększenia.|  
|[CMFCRibbonSlider::OnDraw](#ondraw)|Wywoływane przez platformę, by narysować elementem wstążki. (Przesłania [CMFCRibbonBaseElement::OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw).)|  
|[CMFCRibbonSlider::SetPos](#setpos)|Ustawia bieżący położenie suwaka.|  
|[CMFCRibbonSlider::SetRange](#setrange)|Określa zakres suwaka przez ustawienie wartości minimalną i maksymalną.|  
|[CMFCRibbonSlider::SetZoomButtons](#setzoombuttons)|Pokazuje lub ukrywa przycisków powiększenia.|  
|[CMFCRibbonSlider::SetZoomIncrement](#setzoomincrement)|Określa rozmiar zmiany wielkości dla kontrolki suwaka.|  
  
## <a name="remarks"></a>Uwagi  
 Można użyć `SetRange` metodę, aby skonfigurować zakres zwiększa powiększenie dla suwaka. Bieżąca pozycja suwaka można ustawić przy użyciu `SetPos` metody.  
  
 Przycisków powiększenia cykliczne po lewej i prawej stronie formantu suwaka można wyświetlić przy użyciu `SetZoomButtons` metody. Domyślnie, suwak jest poziomy, przycisku po lewej stronie powiększenie wyświetla znak minus oraz przycisku powiększenie prawy znak plus.  
  
 `SetZoomIncrement` Metoda Określa przyrost do dodania lub odjęcia od bieżącej pozycji, gdy użytkownik kliknie przycisków powiększenia.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia różnych metod w `CMFCRibbonSlider` klasy można ustawić właściwości suwaka. W przykładzie przedstawiono sposób tworzenia `CMFCRibbonSlider` obiekt, wyświetlanie przycisków powiększenia ustawić bieżące położenie suwaka i ustawić zakresu wartości suwaka.  
  
 [!code-cpp[NVC_MFC_RibbonApp#12](../../mfc/reference/codesnippet/cpp/cmfcribbonslider-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxribbonslider.h  
  
##  <a name="cmfcribbonslider"></a>  CMFCRibbonSlider::CMFCRibbonSlider  
 Konstruować suwaka wstążki.  
  
```  
CMFCRibbonSlider(
    UINT nID,  
    int nWidth=100);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nID*  
 Identyfikator suwaka.  
  
 [in]. *nWidth*  
 Szerokość suwak w pikselach.  
  
### <a name="remarks"></a>Uwagi  
 Konstruuje suwaka wstążki, który jest *nWidth* pikseli szerokości w kategorii panelu, gdy suwak jest dodawany. Domyślnie suwak jest poziomy.  
  
##  <a name="getpos"></a>  CMFCRibbonSlider::GetPos  
 Zwraca bieżące położenie suwaka.  
  
```  
int GetPos() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżąca pozycja suwaka, czyli pozycji względem początku suwaka.  
  
##  <a name="getrangemax"></a>  CMFCRibbonSlider::GetRangeMax  
 Pobiera maksymalny przyrost suwak suwak mogą być przesyłane w suwaka.  
  
```  
int GetRangeMax() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Maksymalny przyrost suwak suwak mogą być przesyłane w suwaka.  
  
##  <a name="getrangemin"></a>  CMFCRibbonSlider::GetRangeMin  
 Zwraca minimalną przyrost, który suwak mogą być przesyłane w suwaka.  
  
```  
int GetRangeMin() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Przyrost minimalna suwak mogą być przesyłane w suwaka.  
  
##  <a name="getregularsize"></a>  CMFCRibbonSlider::GetRegularSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *podstawowego kontrolera domeny*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getzoomincrement"></a>  CMFCRibbonSlider::GetZoomIncrement  
 Uzyskaj zmiany wielkości dla kontrolki suwaka.  
  
```  
int GetZoomIncrement() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zmiany wielkości suwaka.  
  
##  <a name="haszoombuttons"></a>  CMFCRibbonSlider::HasZoomButtons  
 Określa, czy suwak ma przycisków powiększenia.  
  
```  
BOOL HasZoomButtons() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli suwak ma przycisków powiększenia; `FALSE` inaczej.  
  
##  <a name="ondraw"></a>  CMFCRibbonSlider::OnDraw  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *podstawowego kontrolera domeny*  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setpos"></a>  CMFCRibbonSlider::SetPos  
 Ustaw bieżącą pozycję suwaka.  
  
```  
void SetPos(
    int nPos,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nPos*  
 Określa położenie do ustawienia dla suwaka. Pozycja jest określana względem początku suwaka.  
  
 [in] *bRedraw*  
 Jeśli `TRUE`, suwak zostanie narysowany ponownie.  
  
##  <a name="setrange"></a>  CMFCRibbonSlider::SetRange  
 Ustaw zakres wartości suwaka.  
  
```  
void SetRange(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nMin*  
 Określa minimalną wartość suwaka.  
  
 [in] *nMax*  
 Określa maksymalną wartość suwaka.  
  
### <a name="remarks"></a>Uwagi  
 Określa zakres wartości dla kontrolki suwaka przez ustawienie wartości minimalną i maksymalną.  
  
##  <a name="setzoombuttons"></a>  CMFCRibbonSlider::SetZoomButtons  
 Wyświetlenie lub ukrycie przycisków powiększenia.  
  
```  
void SetZoomButtons(BOOL bSet=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]. *bUstawienie*  
 `TRUE` Aby wyświetlić przycisków powiększenia; `FALSE` aby je ukryć.  
  
##  <a name="setzoomincrement"></a>  CMFCRibbonSlider::SetZoomIncrement  
 Ustaw zmiany wielkości dla kontrolki suwaka.  
  
```  
void SetZoomIncrement(int nZoomIncrement);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nZoomIncrement*  
 Określa zmiany wielkości suwaka.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)
